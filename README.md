# Decision-Tree-and-Random-Forest
A detailed working of how the decision tree and ensembling techniques work 

Tree 1 -> F1 is the root, F2 and F3 are the leaves (F1- 9y/5n , F2 – 6y/2n, F3 – 3y/3n)
1.	Entropy (Shannon Entropy) (Video)
a.	Helps in calculating the purity of the subset i.e. it helps in understanding whether the subset is pure or not
b.	Splitting in a D-Tree continues till a pure subset is achieved
c.	Value ranges from 0 to 1, Entropy = 1 means completely impure i.e. 50% of both classes, pure subset at Entropy = 0 i.e. just a single class exists in the subset
![image](https://user-images.githubusercontent.com/29723720/117540278-1dcdac80-b02c-11eb-88d5-44e4d647e835.png)


 
d.	Entropy Formula :  H(S) = -P(A)*log2 P(A) - P(B)*log2 P(B)  {For a 2 o/p class subset}
i.	Here H(F2) = -6/8*log26/8 – 2/8*log22/8 = 0.81
ii.	H(F1) = 0.94
iii.	H(F3) = 1

2.	Information Gain (Video)
a.	It is used for deciding what feature is to be used as a root node and what is to be used as leave nodes
b.	Higher the Information Gain , better the split
c.	Formula for calculating Information Gain : 
i.	Gain(S,A) = H(S) -  { [∑|Svalue|/|S|]*H(Svalue) }
ii.	0.91 – (8/14)*0.81 – (6/14)*1
iii.	It can be understood as a method of identifying the split which results in  the maximum entropy reduction so that a system of purity can be reached

3.	Gini Impurity (Video)
a.	Helps in calculating the purity of the subset i.e. it helps in understanding whether the subset is pure or not
b.	Splitting in a D-Tree continues till a pure subset is achieved
c.	GI = 1 - ∑(p^2) = 1 – [ P(A)^2 + P(B)^2]
d.	It is preferred over Entropy because it is computationally efficient
i.	No Log
ii.	Max Value till 0.5
![image](https://user-images.githubusercontent.com/29723720/117540283-27571480-b02c-11eb-8ffc-a729b992d840.png)

 

4.	Splitting Numerical Data (Video)
a.	All the values in the column will be sorted in ASC
b.	A threshold value will be calculated i.e. let’s say a column has data ranging from 
1 to 10, One tree would have threshold as 1 other 2 other 3..and so on 
i.	Hence numerical attributes make the decision tree very slow because for every scenario a tree would be constructed and information gain would be calculated accordingly hence the one with max gain is selected

5.	Measures used for splitting  a tree
a.	ID3 (Iterative Dichotomiser 3)
•	Use Shannon Entropy function and Information gain as metrics only for Classification
•	C4.5 is the successor to ID3 and removed the restriction that features must be categorical by dynamically defining a discrete attribute (based on numerical variables) that partitions the continuous attribute value into a discrete set of intervals.
•	Algorithm creates a multiway tree
b.	CART (Classification and Regression Trees) 
•	Gini Index(Classification) as metric for Classification
•	Reduction in Variance : Used for continuous target variables (regression problems)
•	it constructs binary trees.
•	Obtained tree is pruned by cost-complexity Pruning.

6.	Ensemble Techniques (Video)
a.	It means combining multiple models
b.	Bagging (Bootstrap Aggregation)
i.	Row Sampling with Replacement: Initial Dataset D on a part of which multiple different models will be trained and tested [-> Bootstrap] and a score will be generated or an output class will be declared (in case of classification problems), the mean/median score of all the scores and the highly voted output will be selected in respective scenarios of regression and classification [->Aggregation]

ii.	Note- “With Replacement” means Dataset shared to 2 models is different, there might be some repeated records but not entirely the same
iii.	Random Forest
	Row Sampling with Replacement and Feature Sampling with Replacement: Initial Dataset D on a part of which multiple Decision Tree models will be trained and tested [-> Bootstrap] and a score will be generated or an output class will be declared (in case of classification problems), the mean/median score of all the scores and the highly voted output will be selected in respective scenarios of regression and classification [->Aggregation]
	Whenever a Decision Tree is developed to it’s full depth it is highly overfitted ( Low Bias, High Variance) ; Since in Random Forest the output which is taken is of multiple DTrees (by voting) , High Variance is transformed to Low Variance
	Random Forest can also be used to select the most important features (Article)
iv.	Hard Voting vs Soft Voting
	For Bagging, the final output is selected using voting :
o	Hard Voting: The predicted class label for a particular sample is the class label that represents the majority (mode) of the class labels predicted by each individual classifier.
o	Soft Voting: the output class is the prediction based on the weighted average of probability given to that class. Suppose given some input to three models, the prediction probability for class A = (0.30, 0.47, 0.53) and B = (0.20, 0.32, 0.40). So the average for class A is 0.4333 and B is 0.3067, the winner is clearly class A because it had the highest probability averaged by each classifier.
o	Another Example :
![image](https://user-images.githubusercontent.com/29723720/117540297-38a02100-b02c-11eb-94ae-08b6344cd9b6.png)

 
7.	Pruning
a.	We need to prune the tree in such a way to reduce the prediction error rate by dealing with Overfitting.
b.	Pruning is a technique in machine learning that reduces the size of decision trees by removing sections of the tree that provide little power to classify instances. 
c.	The dual goal of pruning is the reduction complexity of the final classifier as well as better predictive accuracy by the reduction of over-fitting and removal of sections of a classifier that may be based on noisy or erroneous data. 
d.	Pruning is carried out from the leaves to the root.

