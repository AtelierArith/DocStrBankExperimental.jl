```
(new_trace, accepted) = mh(trace, selection::Selection; ..)
(new_trace, accepted) = mh(trace, proposal::GenerativeFunction, proposal_args::Tuple; ..)
(new_trace, accepted) = mh(trace, proposal::GenerativeFunction, proposal_args::Tuple, involution; ..)
```

[`metropolis_hastings`](@ref) のエイリアスです。与えられたトレースに対してメトロポリス・ヘイスティングスの更新を行います。
