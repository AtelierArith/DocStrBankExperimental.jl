```
GeneralizedRandomTessellatedStratified
```

`GeneralizedRandomTessellatedStratified` は、空間的拡散を伴う [`BiodiversityObservationNetwork`](@ref) を生成するための [`BONSampler`](@ref) の一種です。

*引数*:

  * `number_of_nodes`: 選択するサイトの数
  * `grid_size`: 多角形で使用される場合、範囲をカバーするために使用されるグリッドの寸法。GRTS サンプリングは離散的なデカルトインデックスを使用します。

@Olsen

GRTS は、サンプリングドメインのラスタライズされたバージョンの各セルをアドレスで表現し、各セルのアドレスは `D` 桁の4進数で表されます。

`D` の値はラスタのサイズに依存します。GRTS は、ラスタライズされたドメインを再帰的に4つの象限に分割し、その象限をさらに分割して、単一のピクセルに到達するまで続けます。各ステップで、各象限には1、2、3、または4の番号がランダムにラベル付けされます（置換なしで、すべての値が使用されます）。

その後、アドレスは数値的にソートされ、`number_of_nodes` の最小値が選択されます。
