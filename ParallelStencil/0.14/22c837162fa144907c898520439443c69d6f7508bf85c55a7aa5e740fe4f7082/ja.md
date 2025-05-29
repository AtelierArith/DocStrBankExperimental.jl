```
@hide_communication boundary_width block
```

!!! note "Advanced"
    ```
    @hide_communication boundary_width block computation_calls=...
    @hide_communication ranges_outer ranges_inner block
    @hide_communication ranges_outer ranges_inner block computation_calls=...
    ```


計算の背後にある通信をコード `block` の中で隠します。

# 引数

  * `boundary_width::Tuple{Integer,Integer,Integer} | Tuple{Integer,Integer} | Tuple{Integer}`: 各次元の境界の幅。境界は、実行される通信でアクセスされるすべてのデータを（少なくとも）含む必要があります。
  * `block`: 計算を実行するための [`@parallel`](@ref) 呼び出しで始まるコードブロック（例外についてはキーワード `computation_calls` を参照）、続いて境界条件を設定し、通信を実行するためのコード（例えば、パッケージ `ImplicitGlobalGrid` の `update_halo!` など）。計算を実行するための [`@parallel`](@ref) 呼び出しには、通常、位置引数（範囲、nblocks または nthreads）やストリームキーワード引数（stream=...）を含めることはできません（例外についてはキーワード `computation_calls` を参照）。境界条件を設定し、通信を実行するためのコードは、[`@parallel`](@ref) 呼び出しで変更されたフィールドの境界範囲内の要素のみをアクセスする必要があります。すべての要素は他のフィールドからアクセスできます。さらに、このコードには配列ブロードキャスト表記の文を含めることはできません。なぜなら、それらは常にCUDAのデフォルトストリームで実行されるため（CUDA.jl < v2.0）、CUDAストリームのオーバーラップが不可能になるからです。代わりに、境界領域の要素には、境界領域の外の要素にマッピングされるスレッドが起動されないことを保証する範囲引数を渡す [`@parallel`](@ref) 呼び出しを使用してアクセスできます。これらの [`@parallel`](@ref) `ranges` 呼び出しには、他の位置引数（nblocks または nthreads）やストリームキーワード引数（stream=...）を含めることはできません。

!!! note "Advanced"
      * `ranges_outer::`対応する引数の要求に従った1つまたは複数の `ranges` を持つタプル: `ranges` は、実行される通信と境界条件でアクセスされるすべてのデータを（少なくとも）含む必要があります。
      * `ranges_inner::`対応する引数の要求に従った1つまたは複数の `ranges` を持つタプル: `ranges` は、`ranges_outer` に含まれないデータを含む必要があります。


!!! note "Advanced keyword arguments"
      * `computation_calls=1::`通信の背後に隠す計算を含むコード `block` の最初の [`@parallel`](@ref) 呼び出しの数。標準の動作（`computation_calls=1`）から逸脱することが安全であると確信している場合にのみ、この引数を設定してください。多くのシナリオでは、`computation_calls` が `1` より大きい場合、（わずかに）間違った結果が得られることに注意してください。一般的に、境界領域の計算のいかなる点も内部点の計算に依存しない場合にのみ安全です（有限差分導関数は、例えば、間違った結果を引き起こす依存関係を構成する可能性があります）。


# 例

```
@hide_communication (16, 2, 2) begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    update_halo!(Te2);
end

@hide_communication (16, 2) begin
    @parallel diffusion2D_step!(Te2, Te, Ci, lam, dt, dx, dy);
    update_halo!(Te2);
end

@hide_communication ranges_outer ranges_inner begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    update_halo!(Te2);
end

@parallel_indices (iy,iz) function bc_x(A)
    A[  1, iy,  iz] = A[    2,   iy,   iz]
    A[end, iy,  iz] = A[end-1,   iy,   iz]
    return
end
@parallel_indices (ix,iz) function bc_y(A)
    A[ ix,  1,  iz] = A[   ix,    2,   iz]
    A[ ix,end,  iz] = A[   ix,end-1,   iz]
    return
end
@parallel_indices (ix,iy) function bc_z(A)
    A[ ix,  iy,  1] = A[   ix,   iy,    2]
    A[ ix,  iy,end] = A[   ix,   iy,end-1]
    return
end
@hide_communication (16, 2, 2) begin
    @parallel diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    @parallel (1:size(Te,2), 1:size(Te,3)) bc_x(Te);
    @parallel (1:size(Te,1), 1:size(Te,3)) bc_y(Te);
    @parallel (1:size(Te,1), 1:size(Te,2)) bc_z(Te);
    update_halo!(Te2);
end

@hide_communication (16, 2, 2) begin
    @parallel (1:size(Te,1), 1:size(Te,2), 1:size(Te,3)) diffusion3D_step!(Te2, Te, Ci, lam, dt, dx, dy, dz);
    @parallel (1:size(Te,2), 1:size(Te,3)) bc_x(Te);
    @parallel (1:size(Te,1), 1:size(Te,3)) bc_y(Te);
    @parallel (1:size(Te,1), 1:size(Te,2)) bc_z(Te);
    update_halo!(Te2);
end

@hide_communication (16, 2, 2) computation_calls=2 begin
    @parallel computation1!(A2, A, B);
    @parallel computation2!(B, C);
    @parallel (1:size(A,2), 1:size(A,3)) bc_x(A);
    @parallel (1:size(A,1), 1:size(A,3)) bc_y(A);
    @parallel (1:size(A,1), 1:size(A,2)) bc_z(A);
    update_halo!(Te2);
end
```

!!! note "Developers note"
    通信は、計算との最大のオーバーラップを可能にするために、ブロッキング操作を実行してはなりません。


参照: [`@parallel`](@ref)
