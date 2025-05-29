```
AutoBZProblem([rep], f, bz, [p]; kwargs...)
```

BZ積分問題を構築します。

## 引数

  * `rep::AbstractSymRep`: `f`の対称性表現（デフォルト: `UnknownRep()`）
  * `f::AbstractIntegralFunction`: 被積分関数
  * `bz::SymmetricBZ`: 積分を行うブリルアンゾーン
  * `p`: 被積分関数のパラメータ（デフォルト: `NullParameters()`）

## キーワード

追加のキーワードはソルバーに直接渡されます。
