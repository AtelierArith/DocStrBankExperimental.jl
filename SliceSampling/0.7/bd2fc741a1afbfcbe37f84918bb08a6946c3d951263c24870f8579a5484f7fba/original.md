```
Slice(window; max_proposals)
```

Univariate slice sampling with a fixed initial interval (Scheme 2 by Neal[^N2003])

# Arguments

  * `window::Real`: Proposal window.

# Keyword Arguments

  * `max_proposals::Int`: Maximum number of proposals allowed until throwing an error (default: `10000`).
