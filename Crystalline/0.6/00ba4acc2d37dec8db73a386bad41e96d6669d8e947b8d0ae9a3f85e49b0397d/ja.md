```
find_representation(
    symvals::AbstractVector{<:Number}, 
    lgirs::AbstractVector{<:AbstractIrrep},
    assert_return_T::Type{<:Union{Integer, AbstractFloat}}=Int);
    αβγ::Union{AbstractVector{<:Real},Nothing}=nothing,
    atol::Real=DEFAULT_ATOL,
    maxresnorm::Real=1e-3,
    verbose::Bool=false
)                                          --> Union{Nothing, Vector{assert_return_T}}
```

ベクトル（またはベクトルのベクトル）である対称性固有値 `symvals` が、群 gᵢ のすべての操作に沿ってサンプリングされ、`irs` に含まれる不変表現（オプションの自由パラメータ `αβγ` で評価）を持つ場合、各不変表現の重複度を返します。

オプションとして、重複度の要素型は `assert_return_T` 引数を介して指定できます（チェックされた変換を実行し、`assert_return_T` での表現が不可能な場合は `nothing` を返します）。これは、特定のバンドが不変表現の一部のように変換されると疑われる場合に便利です（すなわち、指定された対称性データが不完全である）。

有効な重複度のセットが存在しない場合（すなわち、解決可能であり、実数値および `assert_return_T` で表現可能な型を持つ場合）、センチネル値 `nothing` が返されます。この場合、`verbose=true` を設定することでオプションのデバッグ情報を表示できます。

# 拡張ヘルプ

実際には、各不変表現のキャラクターセット χ⁽ʲ⁾(gᵢ) の投影演算子 P⁽ʲ⁾ を対称性データ sᵢ ≡ `symvals` に適用します：

```
P⁽ʲ⁾  ≡ (dⱼ/|g|) ∑ᵢ χ⁽ʲ⁾(gᵢ)*gᵢ         [キャラクター χ⁽ʲ⁾(gᵢ)、不変表現の次元 dⱼ]
P⁽ʲ⁾s = (dⱼ/|g|) ∑ᵢ χ⁽ʲ⁾(gᵢ)*sᵢ = nⱼ,   [j 番目の不変表現のように変換されるバンドの数]
```

不変表現の重複度 mⱼ ≡ nⱼ/dⱼ を返します。
