```
overapproximate(S::LazySet, T::Type{<:LazySet}, [args]...; [kwargs]...)
```

デフォルトの過大評価メソッドで、`convert`にフォールバックします。

### 入力

  * `X`       – セット
  * `Type{S}` – 対象セットタイプ
  * `args`    – さらなる引数
  * `kwargs`  – さらなるキーワード引数

### 出力

`convert`の結果、またはそのようなメソッドが存在しない場合は`MethodError`。
