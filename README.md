For Developers
============
You can also see [Java](https://github.com/starlangsoftware/NGram), [Python](https://github.com/starlangsoftware/NGram-Py), [Cython](https://github.com/starlangsoftware/NGram-Cy), [Swift](https://github.com/starlangsoftware/NGram-Swift), or [C#](https://github.com/starlangsoftware/NGram-CS) repository.

## Requirements

* [C++ Compiler](#cpp)
* [Git](#git)


### CPP
To check if you have compatible C++ Compiler installed,
* Open CLion IDE 
* Preferences >Build,Execution,Deployment > Toolchain  

### Git

Install the [latest version of Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git).

## Download Code

In order to work on code, create a fork from GitHub page. 
Use Git for cloning the code to your local or below line for Ubuntu:

	git clone <your-fork-git-link>

A directory called DataStructure will be created. Or you can use below link for exploring the code:

	git clone https://github.com/starlangsoftware/NGram-CPP.git

## Open project with CLion IDE

To import projects from Git with version control:

* Open CLion IDE , select Get From Version Control.

* In the Import window, click URL tab and paste github URL.

* Click open as Project.

Result: The imported project is listed in the Project Explorer view and files are loaded.


## Compile

**From IDE**

After being done with the downloading and opening project, select **Build Project** option from **Build** menu. After compilation process, user can run DataStructure-CPP.

Detailed Description
============

+ [Training NGram](#training-ngram)
+ [Using NGram](#using-ngram)
+ [Saving NGram](#saving-ngram)
+ [Loading NGram](#loading-ngram)

## Training NGram
     
Boş bir NGram modeli oluşturmak için
To create an empty NGram model:

	NGram(int N)

For example,

	a = NGram(2);

this creates an empty NGram model.

To add an sentence to NGram:

	void addNGramSentence(Symbol[] symbols)

For example,

	String[] text1 = {"jack", "read", "books", "john", "mary", "went"};
	String[] text2 = {"jack", "read", "books", "mary", "went"};
	nGram = new NGram<String>(2);
	nGram.addNGramSentence(text1);
	nGram.addNGramSentence(text2);

with the lines above, an empty NGram model is created and the sentences text1 and text2 are
added to the bigram model.

NoSmoothing class is the simplest technique for smoothing. It doesn't require training.
Only probabilities are calculated using counters. For example, to calculate the probabilities
of a given NGram model using NoSmoothing:

	a.calculateNGramProbabilities(new NoSmoothing());

LaplaceSmoothing class is a simple smoothing technique for smoothing. It doesn't require
training. Probabilities are calculated adding 1 to each counter. For example, to calculate
the probabilities of a given NGram model using LaplaceSmoothing:

	a.calculateNGramProbabilities(new LaplaceSmoothing());

GoodTuringSmoothing class is a complex smoothing technique that doesn't require training.
To calculate the probabilities of a given NGram model using GoodTuringSmoothing:

	a.calculateNGramProbabilities(new GoodTuringSmoothing());

AdditiveSmoothing class is a smoothing technique that requires training.

	a.calculateNGramProbabilities(new AdditiveSmoothing());

## Using NGram

To find the probability of an NGram:

	double getProbability(Symbol ... symbols)

For example, to find the bigram probability:

	a.getProbability("jack", "reads")

To find the trigram probability:

	a.getProbability("jack", "reads", "books")

## Saving NGram
    
To save the NGram model:

	void saveAsText(String fileName)

For example, to save model "a" to the file "model.txt":

	a.saveAsText("model.txt");              

## Loading NGram            

To load an existing NGram model:

	NGram(String fileName)

For example,

	a = NGram("model.txt");

this loads an NGram model in the file "model.txt".
