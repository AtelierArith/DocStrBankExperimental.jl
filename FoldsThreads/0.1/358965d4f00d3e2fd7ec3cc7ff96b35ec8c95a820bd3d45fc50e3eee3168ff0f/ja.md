```
TaskPoolEx(; [simd,] [basesize,] [ntasks,] [background,])
```

集約のためのプールされたタスクを使用するエグゼキュータ。I/Oを伴う集約やバックプレッシャーの管理に便利です。`background = true`の場合、スループット指向のタスクを隔離し、プライマリスレッドをレイテンシ指向のタスクに使用することもできます。

# 例

```jldoctest TaskPoolEx
julia> using FoldsThreads
       using Folds

julia> Folds.sum(i -> gcd(i, 42), 1:1000_000, TaskPoolEx())
4642844
```

# 拡張ヘルプ

ワーカータスクはプールされている（各エグゼキュータごとに）ため、集約に使用されるJuliaの`Task`の数は`input_length ÷ basesize`よりもはるかに小さくすることができます。この戦略は、負荷分散よりも集約に必要なリソース（例：メモリ）を制限するために主に使用されます。`WorkStealingEx`は、計算集約型の集約の負荷分散に対してより良いパフォーマンスを発揮します。

**注意:** このエグゼキュータは[ThreadPools.jl](https://github.com/tro3/ThreadPools.jl)に触発されています。専用スレッドにタスクを割り当てるためのハックはThreadPools.jlから盗まれたものです。

!!! 警告     **このエグゼキュータをJuliaの*パッケージ*で使用することは強く推奨されません**; 特にライブラリとして使用されるものやエンドユーザーアプリケーションではないものです。このエグゼキュータの目的は、タスク管理のためにJuliaランタイムが正しいことを行うのを*防ぐ*ことだからです。理想的には、ライブラリのユーザーはエグゼキュータを引数として渡すことができるべきであり、あなたのライブラリ関数は`TaskPoolEx`を含む任意のエグゼキュータで使用できるようにするべきです。

## さらなる例

```jldoctest TaskPoolEx
julia> using FoldsThreads
       using FLoops

julia> @floop TaskPoolEx() for x in 1:1000_000
           y = gcd(x, 42)
           @reduce(acc += y)
       end
       acc
4642844
```

## キーワード引数

  * `background = false`: `background == true`の場合、`threadid() == 1`でタスクを実行しません。
  * `ntasks`: 使用するタスクの数。
  * `basesize`: 基本ケースのサイズ。
  * `simd`: `false`、`true`、`:ivdep`、またはそれらのいずれかの`Val`。`true`または`:ivdep`の場合、各基本ケースの最内ループは`@simd`/`@simd ivdep`で注釈されます。`false`（デフォルト）の場合は通常のループを使用します。
