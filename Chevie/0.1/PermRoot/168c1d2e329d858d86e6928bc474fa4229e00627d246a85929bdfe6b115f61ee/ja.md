`action(W::ComplexReflectionGroup,i::Integer,p::Perm)`

`PermRootGroup`の要素は`parent(W)`の根を置換し、すなわち`eachindex(roots(parent(W)))`上の置換です。関数`action`は、`p∈W`のこの作用を`eachindex(roots(W))`に翻訳します。反射部分群の場合、`action(W,i,p)==restriction(W,inclusion(W,i)^p)`となり、親群の場合は`action(W,i,p)==i^p`となります。最初の式は常に有効です。なぜなら、親群の場合`restriction(W)==inclusion(W)==eachindex(roots(W))`だからです。
