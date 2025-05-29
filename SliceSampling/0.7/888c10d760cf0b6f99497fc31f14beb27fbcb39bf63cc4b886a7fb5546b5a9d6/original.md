```
SliceSteppingOut(window; max_stepping_out, max_proposals)
```

Univariate slice sampling by automatically adapting the initial interval through the "stepping-out" procedure (Scheme 3 by Neal[^N2003])

# Arguments

  * `window::Real`: Proposal window.

# Keyword Arguments

  * `max_stepping_out::Int`: Maximum number of "stepping outs" (default: 32).
  * `max_proposals::Int`: Maximum number of proposals allowed until throwing an error (default: `10000`).
