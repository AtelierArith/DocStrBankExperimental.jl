```
(new_trace, accepted) = hmc(
    trace, selection::Selection; L=10, eps=0.1,
    check=false, observations=EmptyChoiceMap())
```

Apply a Hamiltonian Monte Carlo (HMC) update that proposes new values for the selected addresses, returning the new trace (which is equal to the previous trace if the move was not accepted) and a `Bool` indicating whether the move was accepted or not.

Hamilton's equations are numerically integrated using leapfrog integration with step size `eps` for `L` steps. See equations (5.18)-(5.20) of Neal (2011).

# References

Neal, Radford M. (2011), "MCMC Using Hamiltonian Dynamics", Handbook of Markov Chain Monte Carlo, pp. 113-162. URL: http://www.mcmchandbook.net/HandbookChapter5.pdf
