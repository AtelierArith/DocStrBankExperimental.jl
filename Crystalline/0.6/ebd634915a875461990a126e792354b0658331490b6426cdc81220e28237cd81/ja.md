```julia
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep};
    ...
) -> Any
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep},
    bands::AbstractVector{Int64};
    ...
) -> Any
find_representation(
    symeigs::AbstractVector{<:AbstractVector{<:Number}},
    irs::AbstractVector{<:Crystalline.AbstractIrrep},
    bands::AbstractVector{Int64},
    assert_return_T::Type{<:Union{AbstractFloat, Integer}};
    kws...
) -> Any

```

与えられた*バンド*解決対称性固有値 `symeigs`、いくつかの不変量 `irs`、および `symeigs` へのバンドインデックスの選択 `bands` に基づいて、`irs` に対応する関連する重複度を返します。

`symeigs` 引数は、個々のバンドの対称性固有値または対称性キャラクタのベクトルです。`symeigs[n][i]` 番目のエントリは、`n` 番目のバンドと $g_i =$ `group(irs)[i]` 対称操作の対称性固有値 $x_n(g_i)$ を与えます。次のように表されます：

````
```math
x_n(g_i) = \langle \psi_n | g_i | \psi_n \rangle
```
````

設定されていない場合、`bands` は `symeigs` のすべてのバンドを含みます。すなわち、`eachindex(symeigs)` に等しいです。

## キーワード引数

  * `kws`: [`find_representation(::AbstractVector{<:Number})`](@ref) に渡される追加のキーワード引数 (例: `αβγ`, `atol`, `maxresnorm`)。
