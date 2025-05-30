```
WorkStealingEx(; [simd,] [basesize])
```

並列実行のためのワークスティーリングスケジューリング。負荷分散に役立ちます。

# 例

```jldoctest WorkStealingEx
julia> using FoldsThreads
       using Folds

julia> Folds.sum(i -> gcd(i, 42), 1:1000_000, WorkStealingEx())
4642844
```

# 拡張ヘルプ

`WorkStealingEx`は、Transducers.jlおよび他のJuliaFolds/*.jlパッケージのための[ワークスティーリングスケジューラ](https://en.wikipedia.org/wiki/Work_stealing)（特に、[継続スティーリング](https://en.wikipedia.org/wiki/Work_stealing#Child_stealing_vs._continuation_stealing)）を実装しています。ワーカータスクはキャッシュされ再利用されるため、削減に使用されるJulia `Task`の数は`input_length ÷ basesize`よりもはるかに小さくなります。これは、タスクを生成するオーバーヘッドが発生しないため、負荷分散を必要とする計算に良い影響を与えます。

**注意:** `WorkStealingEx`は、デフォルトのマルチスレッドエグゼキュータ`ThreadedEx`よりも複雑で実験的です。

## さらなる例

```jldoctest WorkStealingEx
julia> using FoldsThreads
       using FLoops

julia> @floop WorkStealingEx() for x in 1:1000_000
           y = gcd(x, 42)
           @reduce(acc += y)
       end
       acc
4642844
```

## キーワード引数

  * `basesize`: 基本ケースのサイズ。
  * `simd`: `false`、`true`、`:ivdep`、またはそのいずれかの`Val`。`true`または`:ivdep`の場合、各基本ケースの最も内側のループは`@simd`/`@simd ivdep`で注釈されます。`false`（デフォルト）の場合は通常のループを使用してください。
