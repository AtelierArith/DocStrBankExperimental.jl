```
UnstructuredDomain(dims::NamedTuple; executor=Serial(), header=ComradeBase.NoHeader)
```

次の次元 `dims` から非構造グリッド（実際には点のベクトル）を構築します。`executor` は、`visibilitymap` または `intensitymap` を呼び出すときにグリッドがどのように計算されるかを制御します。デフォルトは `Serial` で、これは通常の CPU 計算を意味します。スレッド実行を使用するには [`ThreadsEx()`](@ref) を使用するか、`OhMyThreads.jl` をロードして彼らのスケジューラを使用します。

`RectiGrid` がグリッドポイントに次元を割り当てるのとは異なり、`UnstructuredDomain` はそうしません。これは、グリッドが非構造的であり、点が空間内のクラウドであるためです。
