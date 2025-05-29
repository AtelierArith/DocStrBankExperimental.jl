```
ensemble_vote(int_img::IntegralArray, classifiers::AbstractArray) -> Integer
```

Classifies given integral image (`IntegralArray`) using given classifiers.  I.e., if the sum of all classifier votes is greater 0, the image is classified positively (1); else it is classified negatively (0). The threshold is 0, because votes can be +1 or -1.

That is, the final strong classifier is

$$
h(x) = \begin{cases}
1&\text{if }\sum_{t=1}^{T}\alpha_{th_{t(x)}}\geq\frac{1}{2}\sum_{t=1}^{T}\alpha_t\\
0&\text{otherwise}
\end{cases}
\text{ where }\alpha_t = \log{\left(\frac{1}{\beta_t}\right)}
$$

# Arguments

  * `int_img::IntegralArray{T, N}`: Integral image to be classified
  * `classifiers::Vector{HaarLikeObject}`: List of classifiers

# Returns

  * `vote::Int8`   1       ⟺ sum of classifier votes > 0   0       otherwise
