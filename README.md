# DOSP-Project1
Distributed implementation of Bitcoin mining using actor model approach and Erlang as programming language.

The goal of this project is to use Erlang and the actor model to build a good solution to the bitcoin mining problem that runs well on multi-core machines.

Bitcoin is a decentralized digital currency that may be exchanged on the peer-to-peer bitcoin network.
Blockchain is a term used to refer to a public distributed ledger where bitcoin transactions are stored and cryptographically validated by network nodes. 
By adopting the alias Satoshi Nakamoto, an unidentified person or group of people created the cryptocurrency in 2008. In 2009, when its implementation was made available as open-source software, the currency was put into use. 
In order to guarantee a finite "supply" of coins, bitcoins leverage the difficulty of cryptographic hashing. This project uses the SHA-256 hash.
Therefore, we must determine the hash values of random strings and check that the number of leading zeros in the hashed value corresponds to the user's input number. We discover a bitcoin only if the input number of zeros and the number of leading zeros in the hash values match.

Group Members:
1) Pavan Appikatla, UFID: 51971306, pappikatla@ufl.edu  
2) Aditya Sure, UFID: 22413121, asure@ufl.edu

Input: The input provided (as command line to project1.erl) will be, the required number of 0’s of the bitcoin.

Output: For each of the bitcoins we mine, print the input string and the accompanying SHA256 hash on separate entry lines, separated by a TAB. Naturally, our SHA256 hash must have the necessary quantity of leading 0s (k=3 in the hash notation indicates 3 number of input 0's). A further need is to prefix the input string with the gator link ID of one of the team members in order to guarantee that each group discovers unique coins.

Project Description:
    It contains the following files:

-clientserver.erl: It is the main file that has the client function as well as the server function. The server spawns workers for mining coins while server is also working to mine coins. When the client is instructed by the server, a worker goes to find a coin and after finding it, the worker sends the coin to the server and the server prints the coin after receiving it.

-projectfile.erl: This file contains the code for cryptographic hashing and mining the coins based on the random strings generated.

How to run:

This project has been developed using VS Code editor.

1.) To initiate the server, execute erl -sname server -setcookie anycookiename. After that compile the clientserver file and startmaster using the command clientserver:startmaster().

2.) To initite the client, execute erl -sname client -setcookie anycookiename. After that start the worker but make sure to send the details of server to it. Use the command clientserver:startworker(name/addressofservernode).

After initialization, the Server starts printing the coins on its own based on the number of inputs given by the user through command line and checks if any workers are available parallelly. Once worker is started, a number of workers are spawned and they request the server for work. If the server finds that a worker is available then the server sends a message to it and makes it mine bitcoins. Once the client finds a bitcoin with matching number of zeros, it sends the bitcoin to the server through a message. Then the server prints the bitcoin of the client while it parallelly prints its own bitcoins. After the client finishes printing, it requests the server again for work.

Machine Specifications: 

Client: Intel(R) Core(TM) i7-8550U
Server: Intel(R) Core(TM) i7-9750H

Size of the work unit:

The size of the work unit refers to the number of sub-problems that a worker gets in a single request from the boss. We were able to do mining with 50 workers and each worker mined 2500 coins. We did this by trial & error basis.

Result of our program for input 4:

pappikatlaSg4iasVE24DO  0000ad757eae95cf7243894e50dfc457f3b3a89ce9e1b3e99d21b6c62214f63c
pappikatlaaVYozcp17RNL  000037170a9659b1ee7c37edaf841b05ce2350b9619907abcd7f6393b8c0e6f0
pappikatlaAVMXXszT0qSD  0000af7e26bf83bfc33e4fd7dc84c5c025339e368817f58574d806bbdb5455c4
pappikatlaVEaGJSBK5bfh  000039425e8a1924902944bb57067a5f6b1e1ac1a0eb88a0792b2544c4a50f49
pappikatlaTEE+ig4gwgef  0000f4596282f38136f35c45b41d7128d625c28926952c4abcd083b780127d94
pappikatlaqyGd2Q9nMpGA  0000e8859990cc8d16c642262c3b361c1e936152cfbb591d8ca46f0085619796

![App Screenshot](https://github.com/adityvardan/DOSP-Project1-Screenshots/blob/8a07aa60d3f314960fa8546517ce5491b2406051/Output%20for%204%20zeros.jpeg)

Running Time:

CPU Time: 2250000
Real Time:  516000
CPU time / Real time: 4.36
![App Screenshot](https://github.com/adityvardan/DOSP-Project1-Screenshots/blob/d43a24bc7bde5e5ec642f968bd98c6ac55c103f7/CPU%20TIME%20VS%20REAL%20TIME.png)

Coin with most zeroes(7):

pappikatlauSgRgug2s00W  0000000f886a637662ed693a552f61163d66115147f49ad5ad4926ddc7843d81
![App Screenshot](https://github.com/adityvardan/DOSP-Project1-Screenshots/blob/7c4c88c92f35bfb942b2f37692a49fdf133409ad/Output%20for%207%20zeros.png)



Max connected working machines:
One server and 3 clients machine were able to be connected. Though we are confident in our capacity to connect more machines, we were unable to do so because there weren't enough resources available.

