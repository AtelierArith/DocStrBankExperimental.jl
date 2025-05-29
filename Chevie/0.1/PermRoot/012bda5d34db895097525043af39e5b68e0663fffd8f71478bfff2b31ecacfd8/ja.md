`restriction(W::PermRootGroup)`

`parent(W)`の各根に対するリストで、根が`W`の根でない場合は`0`、`W`の`i`-番目の根である場合は`i`を保持します。

`restriction(W::PermRootGroup,i::Integer)` `restriction(W::PermRootGroup,v::AbstractVector{<:Integer})`

`restriction(W)[i]`または`restriction(W)[v]`と同じ（ただし、より効率的です）。
