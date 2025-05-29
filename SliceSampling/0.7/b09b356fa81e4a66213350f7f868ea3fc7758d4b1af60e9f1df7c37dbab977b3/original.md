```
SliceDoublingOut(window; max_doubling_out, max_proposals)
```

Univariate slice sampling by automatically adapting the initial interval through the "doubling-out" procedure (Scheme 4 by Neal[^N2003])

# Arguments

  * `window::Real`: Proposal window.

# Keyword Arguments

  * `max_doubling_out`: Maximum number of "doubling outs" (default: 8).
  * `max_proposals::Int`: Maximum number of proposals allowed until throwing an error (default: `10000`).
