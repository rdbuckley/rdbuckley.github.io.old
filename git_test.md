Every day we write repetitive code.
A lot of it is boilerplate that you write only to satisfy your compiler/interpreter:
code that is not related to the main logic of the program like import and export lists, language extensions, file headers.
But how do languages differ in their boilerplate content?
Is it only the content of the boilerplate that changes, or also its quantity?
We explore these questions using data sets of Python and Haskell code.
Besides satisfying our curiosity, we will learn about community-wide habits and realize that after all, repetition is not necessarily uninteresting!

## A first look at the data

<!-- blank line -->
<!-- blank line -->
<figure class="video_container">
  <iframe src="https://www.youtube.com/embed/enMumwvLAug" frameborder="0" allowfullscreen="true"> </iframe>
</figure>
<!-- blank line -->


Our data sets come from public repositories of Haskell and Python packages.
In the case of Haskell, we use a current snapshot of all packages on the [Stackage](http://www.stackage.org) server.
For Python, we downloaded a random subset of approximately 2% of all packages on the [Python Package Index](http://www.pypi.org).
Based on our sample, we estimate the total size of all (compressed!) packages on PyPI to be approximately 19 Gb.
We chose to use only a small sample from PyPI so that we could perform analyses on our laptops.
This sampling allows us to load the Python data set in memory, while keeping its size comparable to the Haskell one.



Let's first look at a few key characteristics of our data sets, namely the number of packages, total number of lines of code (LOC), LOC per package, number of words, and the most common word:

<center>

|                             | Python        | Haskell        |
| --------------------------- | ------------- | -------------- |
| **Number of packages**      | 3414          | 2312           |
| **LOC**                     | 6,048,755     | 3,862,107      |
| **Average LOC per package** | 1772          | 1760           |
| **Number of words**         | 36,577,867    | 23,174,821     |
| **Most common word**        | `x` (6,7%)    | `NUL` (4,5%)   |

</center>

Hold on! `NUL` is the most common word in Stackage packages? Surprising, but true: `\NUL` is the quotation of the null character, and a small number of packages (2.7%) have inline byte strings with many, many copies of `\NUL` in them.
The next common Haskell word is "a", which is a common type and term variable name.
It is also interesting to see that the average number of lines of code is very, very similar in the Haskell and the Python data sets!
