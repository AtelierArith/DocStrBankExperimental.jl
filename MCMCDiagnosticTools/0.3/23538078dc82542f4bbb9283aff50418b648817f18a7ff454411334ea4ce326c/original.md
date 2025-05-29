```
rafterydiag(
    x::AbstractVector{<:Real}; q=0.025, r=0.005, s=0.95, eps=0.001, range=1:length(x)
)
```

Compute the Raftery and Lewis diagnostic [^Raftery1992]. This diagnostic is used to determine the number of iterations required to estimate a specified quantile `q` within a desired degree of accuracy.  The diagnostic is designed to determine the number of autocorrelated samples required to estimate a specified quantile $\theta_q$, such that $\Pr(\theta \le \theta_q) = q$, within a desired degree of accuracy. In particular, if $\hat{\theta}_q$ is the estimand and $\Pr(\theta \le \hat{\theta}_q) = \hat{P}_q$ the estimated cumulative probability, then accuracy is specified in terms of `r` and `s`, where $\Pr(q - r < \hat{P}_q < q + r) = s$. Thinning may be employed in the calculation of the diagnostic to satisfy its underlying assumptions. However, users may not want to apply the same (or any) thinning when estimating posterior summary statistics because doing so results in a loss of information. Accordingly, sample sizes estimated by the diagnostic tend to be conservative (too large).

Furthermore, the argument `r` specifies the margin of error for estimated cumulative probabilities and `s` the probability for the margin of error. `eps` specifies the tolerance within which the probabilities of transitioning from initial to retained iterations are within the equilibrium probabilities for the chain. This argument determines the number of samples to discard as a burn-in sequence and is typically left at its default value.

[^Raftery1992]: A L Raftery and S Lewis. Bayesian Statistics, chapter How Many Iterations in the Gibbs Sampler? Volume 4. Oxford University Press, New York, 1992.
