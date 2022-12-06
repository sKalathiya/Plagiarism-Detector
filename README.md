# Plagiarism-Detector
Plagiarism Detector using the Rabin karp algorithm.


I implemented the "Plagiarism Detector Project" on the basis of Rabin-Karp Algorithm for both the source code as well as text.

There are total of 4 steps in this project:

1) PreProcessing Text
2) Creating HashList
3) Comparing the HashList
4) Computing the Similarity Percentage

1) PreProcessing Text

So,the algorithm reads the file into a string and then preprocess it.
  -  Lowercase the String
  -  Tokenzie the strings into array of words using the pattern "\\W+"
  -  Remove the words present in the "StopWords" list and the words which consists of only digits
  -  Concate the words into a single string

At last,we have a Processed String.


2) Creating HashList

Algorithm creates a list of hash using the processed string.
It uses the rolling hash as to reduce the execution time.
So the hash function that it uses is:
	
	 hashN = ((hashp - (procText.charAt(i) )  * Math.pow(b,kgram-1)) * b )+ (procText.charAt(j) )

Here, hashp = previous hash
	hashN = new hash
	procText = processed String
	i = first character of previous hash
	j = last character of new hash
	b = base(it is 271 in this algorithm)
	kgram = length of the string that it takes to create 1 hash( 5 in our case)
	
It uses the previous hash that we calculated.It removes the first character and then adds the new character to 
create a new hash.

Also,for big file we module the function to avoid overflow of integer.We used (5849) in our case.
So,at last we have a list of all the hash calculated with the processed string.


3) Comparing the HashList

Here,we compare both the hashlist of the documents.
We check for a common hash in both the list and increase the counter.


4) Computing

Herw, with the help of common counter we calculate the similarity percentage of both the documents.
There are many foemulas for this but the one that we use here is:

	Per = (2 * common) / (a + b)) * 100
where,
	Per = percentage
	common = common counter
	a = size of text1 hash list
	b = size of text2 hash list

At last we have the percentage of similarity between both the documents.
If the percentage is above 46.5 we return "1" which means it is plagiarised.
and if it is less we return "0" which means it is not plagiarised.

	  
