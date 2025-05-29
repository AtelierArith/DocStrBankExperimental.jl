Uses different strategies to compute power norm bounds.

If specified, `m` norms of powers are estimated computationally, and then `m_extend` norms are obtained with a cheaper refinement process. Otherwise these numbers are selected automatically.

A vector of length m*extend is returned, such that norms[k] ≥ ||Q*h^k|*{U*h^0}||
