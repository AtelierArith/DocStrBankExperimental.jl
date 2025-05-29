```
マクロ >(body)
```

bodyが`object_ |> call_`の形である場合、`call`に対して[`@_`](@ref)を呼び出し、`object`に再帰します。

```jldoctest chain
julia> using LightQuery


julia> @> 0 |> _ - 1 |> abs |> Base.abs
1
```

複数の引数を含めることはできません。

```jldoctest chain
julia> @> _ |> _ + __
ERROR: LoadError: ArgumentError: Chain segments must contain single underscores only
[...]
```

チェーンをネストすることができます：

```jldoctest chain
julia> @> 1 |> (@> _ + 1 |> _ + 1)
3
```

補間をシームレスに処理します：

```jldoctest chain
julia> @> 1 |> :(_ + $_)
:(_ + 1)
```
