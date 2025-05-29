```julia
est_doa(
    manifold,
    reduction_function;
    init_az,
    init_el,
    kwargs...
)

```

マニフォールド `manifold` に関して到着方向 (DOA) を計算します。計算された DOA は `Spherical` オブジェクトとして返され、方位角は x 軸から反時計回りに数えられ、高度は xy 平面から天頂に向かって数えられます。初期方位角 `init_az` と高度 `init_el` が提供されると、ヒルクライミングアルゴリズムが使用されます。ヒルクライミングアルゴリズムは単純な最大探索よりもはるかに速いはずですが、局所的な最大値しか見つけられない可能性があり、これは望ましい場合もあります。

# 例

信号サブスペースを使用する場合:

```julia-repl
julia> est_doa(manifold, a -> norm(signal_subspace' * a) / norm(a))
```

ノイズサブスペース (MUSIC) を使用する場合:

```julia-repl
julia> est_doa(manifold, a -> norm(a) / norm(noise_subspace' * a))
```

# 引数:

  * `manifold::AbstractManifold`: アンテナアレイのマニフォールド
  * `reduction_function`: マニフォールドベクトルをスカラーに減少させる関数
