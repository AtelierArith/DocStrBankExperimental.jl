```
BoundedPointProcess{M,P,T} <: AbstractPointProcess{M}
```

事前に定義された開始時刻と終了時刻を持つ時間的点過程 `P`。

少ない引数を受け入れる `AbstractPointProcess` インターフェースのためのいくつかのフォールバックを実装します。

# フィールド

  * `pp::P`: 基本となる点過程
  * `tmin::T`: 開始時刻
  * `tmax::T`: 終了時刻
