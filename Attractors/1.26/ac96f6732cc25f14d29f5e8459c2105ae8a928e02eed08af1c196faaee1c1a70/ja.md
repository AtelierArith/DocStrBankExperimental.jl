```
MCSBlackBoxOptim(; kwargs...)
```

[`minimal_critical_shock`](@ref)で使用されるブラックボックスの導関数フリー最適化アルゴリズムです。

## キーワード引数

  * `guess = nothing`: 最適化アルゴリズムに与えられる最小クリティカルショックの初期推測。`nothing`でない場合、以下の`random_algo`は無視されます。
  * `max_steps = 10000`: 最適化アルゴリズムの最大ステップ数。
  * `penalty = 1000.0`: 異なるアトラクションの盆地に至らない摂動に対する目的関数のペナルティ値。この値は摂動のノルムに加算され、その値はアトラクションの盆地の典型的なサイズよりもはるかに大きい必要があります。
  * `print_info`: ブール値、trueの場合、最適化アルゴリズムは目的関数の評価ステップに関する情報を印刷します。`default = false`。
  * `random_algo = MCSBruteForce(100, 100, 0.99)`: 初期推測を提供するために使用できる[`MCSBruteForce`](@ref)のインスタンス。
  * `bbkwargs = NamedTuple()`: ソルバー、精度などを選択するために`BlackBoxOptim.bboptimize`に伝播される追加のキーワード引数。

## 説明

このアルゴリズムはBlackBoxOptim.jlを使用し、最小化するためのペナルティ付き目的関数を使用します。制約関数として使用されるy関数。したがって、探索中に別の盆地に到達した場合、アルゴリズムを奨励し、そうでない場合はペナルティで罰します。最小化する関数は（いくつかの詳細を除いて）次の通りです：

```julia
function mfs_objective(perturbation, u0, mapper, penalty)
    dist = norm(perturbation)
    if mapper(u0 + perturbation) == mapper(u0)
        # 同じ盆地に留まる場合はペナルティを課す:
        return dist + penalty
    else
        return dist
    end
end
```

初期推測を使用することは、パフォーマンスと精度の両方に有益であるため、粗い[`MCSBruteForce`](@ref)の出力が推測を提供するために使用されます。これは、`guess`ベクトルを明示的に渡すか、`random_algo`として`nothing`を指定することで無効にできます。
