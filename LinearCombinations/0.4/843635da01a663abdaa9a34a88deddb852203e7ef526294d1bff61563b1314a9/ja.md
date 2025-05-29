```
LinearCombinations.linear_filter(x) -> Bool
```

`x` が線形結合に格納されるべきであれば `true` を返し、削除されるべきであれば `false` を返します。

これにより、線形結合はすべての可能な項によって張られるベクトル空間（または自由モジュール）ではなく、`linear_filter` が `false` を返す項によって張られる部分空間（または部分モジュール）による商に存在します。除外される項に対して係数を設定することは許可されていますが、効果はありません。

`linear_filter` のデフォルトの返り値はすべての引数に対して `true` であるため、何も除外されません。

関連情報として [`keeps_filtered`](@ref)、[`LinearCombinations.termcoeff`](@ref) を参照してください。

# 例

```julia-repl
julia> LinearCombinations.linear_filter(x::Char) = islowercase(x)

julia> a = Linear('x' => 1, 'Y' => 2)
x

julia> a['Z'] = 3
3

julia> a
x
```
