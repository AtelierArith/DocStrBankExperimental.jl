```
allocate_input(p::PencilFFTPlan)          -> PencilArray
allocate_input(p::PencilFFTPlan, dims...) -> Array{PencilArray}
allocate_input(p::PencilFFTPlan, Val(N))  -> NTuple{N, PencilArray}
```

与えられたプランの入力データを保持できる初期化されていない [`PencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.PencilArray) を割り当てます。

第二および第三の形式は、それぞれサイズ `dims` の `PencilArray` の配列と、`N` の `PencilArray` のタプルを割り当てます。

!!! note "インプレースプラン"
    `p` がインプレースの実数から実数、または複素数から複素数のプランである場合、[`ManyPencilArray`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#PencilArrays.ManyPencilArray) が割り当てられます。`p` がインプレースの実数から複素数のプランである場合、[`ManyPencilArrayRFFT!`](@ref) が割り当てられます。

    これらの型は、同じメモリ空間を共有する入力および出力変換（および中間変換）のための `PencilArray` ラッパーを保持します。入力および出力の `PencilArray` は、それぞれ [`first(::ManyPencilArray)`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#Base.first-Tuple{ManyPencilArray}) と [`last(::ManyPencilArray)`](https://jipolanco.github.io/PencilArrays.jl/dev/PencilArrays/#Base.last-Tuple{ManyPencilArray}) を呼び出すことでアクセスする必要があります。

    #### 例

    `p` がインプレースの `PencilFFTPlan` であるとします。すると、

    ```julia
    @assert is_inplace(p)
    A = allocate_input(p) :: ManyPencilArray
    v_in = first(A)       :: PencilArray  # 入力データビュー
    v_out = last(A)       :: PencilArray  # 出力データビュー
    ```

    また、インプレースプランは返された `ManyPencilArray` に対して直接実行する必要があり、含まれている `PencilArray` ビューに対しては実行できません：

    ```julia
    p * A       # インプレースで前方変換を実行
    p \ A       # インプレースで後方変換を実行
    # p * v_in  # 許可されていません!!
    ```

