# Lab-15-Bias-Variance-Tradeoff
The Bias-Variance Tradeoff: Choosing How Flexible a Model Should Be
Objective

I wanted to see how a model's flexibility affects its error on new data, and to find out whether cross-validation can pick a good level of flexibility and give an honest estimate of that error.

Methodology
I worked in a simulated world where the true curve is known, so every fit could be checked against it.
For six polynomial degrees, I fit 200 fresh samples and split the error into bias squared and variance.
For degrees 1 to 15, I compared training error with error on 2,000 new points and found the degree where the held-out error was lowest.
I used 5-fold cross-validation on the training points to choose a degree, and looked at how much the error changed from fold to fold.
I used nested cross-validation to check whether the smallest CV error is a fair estimate of the error on new data.
I wrote a small function, kfold_mse(), that returns the k-fold CV error for any degree and number of folds, and I used it to rerun the comparison with 10 folds.
For the take-home challenge, I fit polynomials with more coefficients than training points, using the minimum-norm fit, and tracked training and held-out error well past the interpolation point.
Key Findings
Variance was 0.0180 at degree 5 and 0.0994 at degree 15, so the most flexible model moved the most from sample to sample.
Held-out error on the 2,000 new points was lowest at degree 5. Training error kept falling as the degree went up, so it was no help for choosing a degree.
5-fold CV chose degree 4, with a CV MSE of 0.1401.
The nested CV estimate was 0.2070, higher than 0.1401. The smallest CV error is too optimistic because the same scores were used to choose the degree.
With 10 folds, the CV MSE was 0.1409 for degree 4 and 0.1457 for degree 5. Degree 4 came out ahead again, but the gap between the two is small.
Challenge: [YOUR RESULT]
