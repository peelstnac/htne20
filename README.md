# Book.it!
> Discover old classics that Google has forgotten.

## Motivation
Sometimes, with a vague description, it is difficult to successfully find the title of an older book on Google. This is where Book.it! comes in. With a couple optimized algorithms and a database of over 15,000 titles that go way back into the 1800s, Book.it can find that one old classic you simply cannot find with your Google search.

## Method
We precompute the frequency of each word in the plot summaries of each title and stor the information in a list of dictionaries. We serialize this variable with [pickle](https://docs.python.org/3/library/pickle.html). For each query,
1. The terms are split into individual words.
2. For each title, the [tf-idf](https://en.wikipedia.org/wiki/Tf%E2%80%93idf) value of each term is calculated.
3. A score is assigned to each title, being the sum of tf-idf values for each search term.
4. Titles are sorted by tf-idf values.
5. The top 20 results are taken. We calculate the [longest common subsequence](https://en.wikipedia.org/wiki/Longest_common_subsequence_problem) (an element in the sequence is a word) between the search terms and each title's summary. Using that metric, we finally reorder the top 20 results.
