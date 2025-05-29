```
TensorMap(data::AbstractArray, codomain::ProductSpace{S,N₁}, domain::ProductSpace{S,N₂};
                tol=sqrt(eps(real(float(eltype(data)))))) where {S<:ElementarySpace,N₁,N₂}
TensorMap(data, codomain ← domain; tol=sqrt(eps(real(float(eltype(data))))))
TensorMap(data, domain → codomain; tol=sqrt(eps(real(float(eltype(data))))))
```

平面多次元配列から `TensorMap` を構築します。

## 引数

  * `data::DenseArray`: プレーン配列としてのテンソルデータ。
  * `codomain::ProductSpace{S,N₁}`: `N₁` 個の `S<:ElementarySpace` 型の空間の `ProductSpace` としてのコドメイン。
  * `domain::ProductSpace{S,N₂}`: `N₂` 個の `S<:ElementarySpace` 型の空間の `ProductSpace` としてのドメイン。
  * `tol=sqrt(eps(real(float(eltype(data)))))::Float64`:

ここで、`data` は三つの方法で指定できます。

1. `data` は長さ `dim(codomain ← domain)` の `DenseVector` であることができ、その場合、テンソルマップの実際の独立エントリを表します。`data` を直接参照するインスタンスが作成されます。
2. `data` はサイズ `(dim(codomain), dim(domain))` の `AbstractMatrix` であることができます。
3. `data` はランク `N₁ + N₂` の `AbstractArray` であり、ドメインとコドメイン空間のサイズに一致する必要があります。すなわち、`size(data) == (dims(codomain)..., dims(domain)...)` です。

ケース 2 と 3 の場合、`TensorMap` コンストラクタはテンソルデータを再構築し、結果として得られるテンソル `t` が `data == convert(Array, t)` を満たすようにします。誤差は `tol` で指定されます。`sectortype(S) == Trivial` であり、`data` が `DenseArray` の場合、`data` 配列は単にベクトルに再形成され、ケース 1 のように使用されるため、メモリは共有されます。他のケースでは、新しいメモリが割り当てられます。

`N₁ + N₂ = 1` の場合、ケース 3 も `data` がベクトルであることを意味しますが、`N₁ + N₂ == 2` の場合、ケース 2 とケース 3 の両方で `data` が行列である必要があります。このような曖昧なケースは、すべての可能なケースをサポートするために `data` のサイズを確認することで解決されます。

!!! note
    ケース 2 と 3 のこのコンストラクタは、プレーン配列への変換が可能な `sectortype` 値に対してのみ機能し、`data` が実際に指定された対称構造を尊重する場合にのみ、許容誤差 `tol` まで機能します。

