要素ごとにおよび再帰的に `Tuple`、`NamedTuple`、`SArray`、および `ForwardDiff.Dual` 数に対して動作するブロードキャスト関数を実装します。

```
関数は次のとおりです：
- `badd` (ブロードキャスト加算)
- `bsub` (ブロードキャスト減算)
- `bmul` (ブロードキャスト乗算)
- `bdiv` (ブロードキャスト除算)
- `bmax` (ブロードキャスト最大)
- `bmin` (ブロードキャスト最小)
```

再帰的であるため、`bmul(a, b)` は必ずしも `map(*, a, b)` と同じことをするわけではありません。たとえば、`a` と `b` が `SMatrices` のタプルである場合、`bmul` は要素ごとにそれらを乗算しますが、`map` は行列としてそれらを乗算します。これは、`bmul` が `a` と `b` の要素に対して `bmul` を呼び出すのに対し、`map` は `a` と `b` の要素に対して `*` を呼び出すためです。
