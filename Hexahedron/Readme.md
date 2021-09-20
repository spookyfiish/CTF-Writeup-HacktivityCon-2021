# H@cktivityCon: Hexahedron
 
![warmup category](https://img.shields.io/badge/Category-Cryptography-brightgreen.svg)  
![score](https://img.shields.io/badge/Score_after_CTF-50-blue.svg)  
![solves](https://img.shields.io/badge/Solves-260-lightgrey.svg) 

## Description
So much of crypto is all about shapes! Since some shapes have so many special sides :)

## Attached files
- hexahedron.txt

## Summary
I used the RsaCtfTool.

## Flag
```
flag{080eaeb0d8f724bcb542562b3bb708e5}
```

## Detailed solution
The file contains the public key (n, e) and the ciphered text c:
```
n = 0x9ffa2a58ad286990fc5fe97b669e8cb2752e81fafa5ac774ea856d8ca124089ba4b06fe21a5d588c1dcb9602838d32cd70e50b85dec21fa79944543176c7a3b8b804ab754af2978f23b09f2905103dd5a4c748df8d9e9a079a5b38f6f69051b3c6582ebc2d2d199b3a97cb7e58af79b90fe08884626d188e194816bd51960a45
e = 0x3
c = 0x10652cdfaa6a6f6f688b98219cd32ce42c4d4df94afaea31cd94dfac50678b1f50f3ab1fd389f9998b6727ffd1a2c06ee6bde21ae85daef63fd0fa694a93f3674dc3f9ea0f2e3283a3d9897137aea12458aa3b8f96c61f3bf74a510bab7e7d8b7af52290d2621f1e06e52e6a7be4896c6465
```
I intended to use RsaCtfTool to solve this challenge, however I wasn't sure if it would accept hex numbers, so I converted them to integers.
```
n = "0x9ffa2a58ad286990fc5fe97b669e8cb2752e81fafa5ac774ea856d8ca124089ba4b06fe21a5d588c1dcb9602838d32cd70e50b85dec21fa79944543176c7a3b8b804ab754af2978f23b09f2905103dd5a4c748df8d9e9a079a5b38f6f69051b3c6582ebc2d2d199b3a97cb7e58af79b90fe08884626d188e194816bd51960a45"
c = "0x10652cdfaa6a6f6f688b98219cd32ce42c4d4df94afaea31cd94dfac50678b1f50f3ab1fd389f9998b6727ffd1a2c06ee6bde21ae85daef63fd0fa694a93f3674dc3f9ea0f2e3283a3d9897137aea12458aa3b8f96c61f3bf74a510bab7e7d8b7af52290d2621f1e06e52e6a7be4896c6465" 

print(int(n, 16))
print(int(c, 16))
```
I then ran the tool (the format is ```python3 RsaCtfTool.py -n {n} -e {e} --uncipher {c}```).
```
$ python3 RsaCtfTool.py -n 112339816301925396926211289689793745814213925314273886071305785874178028552510482239036537066616690493241410015435402110525284201411608164205573122430898583517515498250410244592963132324072861567753086739636553410154316180827724708002409356129254383468446158145079982391991062389788544378839486986385137994309 -e 3 --uncipher 2217344750798178599616518881851238192046537371134831984828894413752520937378161486880269974456574131502921272953104454680926482208357166098075344508240480152890914678813031666242202555794691235412837030045499161787224264164243336308650477343133919653356349913604131486721125
```
And got the flag from the output:
```
Unciphered data :
HEX : 0x666c61677b30383065616562306438663732346263623534323536326233626237303865357d
INT (big endian) : 13040004482819483500695568095911430044119005002403329881609730936713446088302388627030488445
INT (little endian) : 15940898332589092471641868064009868552823996352415667103914137547565850266448879169635970150
utf-8 : flag{080eaeb0d8f724bcb542562b3bb708e5}
utf-16 : 汦条ほ〸慥扥搰昸㈷戴扣㐵㔲㈶㍢扢〷攸紵
STR : b'flag{080eaeb0d8f724bcb542562b3bb708e5}'
```
The flag is:
```
flag{080eaeb0d8f724bcb542562b3bb708e5}
```