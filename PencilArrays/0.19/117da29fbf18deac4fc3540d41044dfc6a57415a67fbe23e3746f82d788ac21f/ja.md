```
PencilArray(pencil::Pencil, data::AbstractArray{T,N})
```

鉛筆分解情報を持つ配列ラッパーを作成します。

配列の次元と要素の型は、与えられた鉛筆のそれと一致している必要があります。

!!! note "インデックスの順序"
    `Pencil` に関連付けられたインデックスの順序がある場合、`data` はそれに応じて次元が順序変更されている必要があります（*メモリ*順序で）。

    `data` とは異なり、結果の `PencilArray` は順序変更されていないインデックス（*論理*順序で）でアクセスする必要があります。

    ##### 例

    `pencil` が順序変更前にローカル次元 `(10, 20, 30)` を持ち、関連付けられた順序が `(2, 3, 1)` であるとします。すると：

    ```julia
    data = zeros(20, 30, 10)       # 親配列（メモリ順序での次元を持つ）

    u = PencilArray(pencil, data)  # 次元が (10, 20, 30) のラッパー
    @assert size_local(u) === (10, 20, 30)

    u[15, 25, 5]          # BoundsError (15 > 10 および 25 > 20)
    u[5, 15, 25]          # 正しい
    parent(u)[15, 25, 5]  # 正しい

    ```


!!! note "追加次元"
    データ配列は、右側に1つ以上の追加次元を持つことができ、これらはインデックスの順序変更の影響を受けません。

    ##### 例

    ```julia
    dims = (20, 30, 10)
    PencilArray(pencil, zeros(dims...))        # 動作します（スカラー）
    PencilArray(pencil, zeros(dims..., 3))     # 動作します（3成分ベクトル）
    PencilArray(pencil, zeros(dims..., 4, 3))  # 動作します（4×3 テンソル）
    PencilArray(pencil, zeros(3, dims...))     # 失敗します
    ```


---

```
PencilArray{T}(undef, pencil::Pencil, [extra_dims...])
```

ローカル鉛筆にデータを保持できる未初期化の `PencilArray` を割り当てます。

ベクトル成分を表す追加次元を指定できます。これらの次元は、結果の配列の最も右側（最も遅い）インデックスに追加されます。

# 例

`pencil` がローカル次元 `(20, 10, 30)` を持つとします。すると：

```julia
PencilArray{Float64}(undef, pencil)        # 配列の次元は (20, 10, 30)
PencilArray{Float64}(undef, pencil, 4, 3)  # 配列の次元は (20, 10, 30, 4, 3)
```

さらに例：

```jldoctest
julia> pen = Pencil((20, 10, 12), MPI.COMM_WORLD);

julia> u = PencilArray{Float64}(undef, pen);

julia> summary(u)
"20×10×12 PencilArray{Float64, 3}(::Pencil{3, 2, NoPermutation, Array})"

julia> PencilArray{Float64}(undef, pen, 4, 3) |> summary
"20×10×12×4×3 PencilArray{Float64, 5}(::Pencil{3, 2, NoPermutation, Array})"

```
