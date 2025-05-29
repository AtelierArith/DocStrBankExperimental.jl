```
fixedpoints(ds::CoreDynamicalSystem, box, J = nothing; kwargs...) → fp, eigs, stable
```

与えられたアウトオブプレイス `ds`（`DeterministicIteratedMap` または `CoupledODEs` のいずれか）のすべての固定点 `fp` を、パラメータ設定 `p` に対して状態空間の部分集合 `box` 内に存在するものとして返します。固定点は [`StateSpaceSet`](@ref) として返されます。便利のために、各固定点のヤコビ行列の固有値のベクトルと、固定点が安定かどうかも返されます。

`box` は、IntervalRootFinding.jl からの適切な区間ボックス（区間のベクトル）です。例えば、3Dシステムの場合は次のようになります。

```julia
v, z = interval(-5, 5), interval(-2, 2)  # 1D intervals
box = [v, v, z]
```

`J` は `ds` の動的ルールのヤコビ行列です。これは [`TangentDynamicalSystem`](@ref) のようなものですが、この場合、自動ヤコビ行列推定は機能しないため、手動でコーディングされたバージョンを提供する必要があります。

内部的には IntervalRootFinding.jl が使用されており、その結果、安定性に関係なく `box` 内に存在するすべての固定点を見つけることが保証されています。IntervalRootFinding.jl はユニークな固定点を含む区間を返すため、区間の中点を実際の固定点として返します。もちろん、IntervalRootFinding.jl に固有の制限がここでも適用されます。

`fixedpoints` の出力は、[BifurcationKit.jl](https://github.com/rveltz/BifurcationKit.jl) の継続プロセスの開始点として使用できます。さらに [`periodicorbits`](@ref) も参照してください。

## キーワード引数

  * `method = IntervalRootFinding.Krawczyk` は、ルート探索メソッドを設定します。IntervalRootFinding.jl のドキュメントで可能なすべての選択肢を参照してください。
  * `tol = 1e-15` は、ルート探索の許容誤差です。
  * `warn = true` は、固定点が見つからない場合に警告を投げます。
  * `order = nothing` は、[`DeterministicIteratedMap`](@ref) の n 番目の反復の固定点を検索します。正の整数または `nothing` でなければなりません。元のマップの固定点を検索するには、`nothing` または 1 を選択してください。

## パフォーマンスノート

`order` を 5 より大きい値に設定すると非常に遅くなる可能性があります。[`periodicorbits`](@ref) のような周期軌道検出により適したアルゴリズムの使用を検討してください。
