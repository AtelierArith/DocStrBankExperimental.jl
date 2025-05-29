```
regroup(a, b) -> Regroup
```

`Regroup`オブジェクトを返し、テンソルやその他の構造のコンポーネントを再配置するために使用できます。

実際の再配置は、2つのパラメータ`a`と`b`によって指定されます。両方は整数のネストされたタプルからなる式木です。これらの木はネストされたテンソルの構造をエンコードし、整数はネストされたソーステンソルのコンポーネントからネストされたターゲットテンソルへのマッピングを指定します。`a`と`b`のラベルは実際には`Int`の代わりに任意の`isbits`型であることができますが、`a`と`b`では同じでなければなりません。

返り値`rg = regroup(a, b)`は呼び出し可能なオブジェクトです。`rg`の引数`t`は`a`ツリーと同じ形状のネストされたテンソルでなければならず、返り値は`b`と同じ形状の`Tensor`です。ネストされたテンソル`t`のコンポーネントはラベルに従って置換されます。

`t`のコンポーネントにゼロでない次数がある場合、`rg(t)`は通常の符号ルールに従って符号を持ちます：2つのオブジェクト`x`と`y`が入れ替わると、符号`(-1)^(deg(x)*(deg(y)))`が発生します。

さらに、`rg`は線形であり、テンソルの線形結合で呼び出すことができます。

各`Regroup`要素`rg`について、Juliaは`rg(t)`を計算するための別々で効率的なコードを生成することに注意してください。

他にも[`swap`](@ref)、[`regroup_inv`](@ref)、[`Regroup`](@ref)、[`LinearCombinations.DefaultCoefftype`](@ref)を参照してください。

# 例

# 次数なしの例

```jldoctest regroup
julia> rg = regroup(:( (1, (2, 3), 4) ), :( ((3, 1), (4, 2)) ))
Regroup{(1, (2, 3), 4),((3, 1), (4, 2))}

julia> t = Tensor("x", Tensor("y", "z"), "w")
"x"⊗("y"⊗"z")⊗"w"

julia> rg(t)
Linear1{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 1 term:
("z"⊗"x")⊗("w"⊗"y")
```

# 次数ありの例

簡単のため、`String`の次数をその長さと定義します。

```jldoctest regroup
julia> LinearCombinations.deg(x::String) = length(x)

julia> rg(t)   # 同じrgとt
Linear1{Tensor{Tuple{Tensor{Tuple{String, String}}, Tensor{Tuple{String, String}}}}, Int64} with 1 term:
-("z"⊗"x")⊗("w"⊗"y")
```
