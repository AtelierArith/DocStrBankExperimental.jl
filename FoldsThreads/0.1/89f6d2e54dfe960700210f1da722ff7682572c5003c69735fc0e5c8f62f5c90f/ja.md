```
NondeterministicEx(; [simd,] [basesize,] [ntasks,])
```

非並列化コレクション（例：`Channel`、`Iterators.Stateful`）を用いた計算を並列化するためのパイプライン化されたバッチ削減。

これは[`NondeterministicThreading`](https://juliafolds.github.io/Transducers.jl/dev/reference/manual/#Transducers.NondeterministicThreading)トランスデューサのシンプルなラッパーです。並列化されるトランスデューサを明示的に制御するには、`NondeterministicThreading`を直接使用してください。

# 例

```jldoctest NondeterministicEx
julia> using FoldsThreads
       using Folds

julia> partially_parallelizable(seq) = (gcd(y, 42) for x in seq for y in 1:10000x);

julia> Folds.sum(partially_parallelizable(Iterators.Stateful(1:100)), NondeterministicEx())
234462500
```

# 拡張ヘルプ

上記の例では、`gcd(y, 42)`（マッピング）、`for y in 1:10000x`（フラット化）、および`+`による`sum`（削減）を並列に実行できますが、`Iterators.Stateful(1:100)`の反復は並列化できません。例に示されているように、非並列化コレクションの各反復ごとの計算は、`NondeterministicEx`が何らかのパフォーマンス向上を示すために非常にCPU集約的である必要があります。

FLoops.jlを使用した同じ計算：

```jldoctest NondeterministicEx
julia> using FoldsThreads
       using FLoops

julia> @floop NondeterministicEx() for x in Iterators.Stateful(1:100)
           for y in 1:10000x
               z = gcd(y, 42)
               @reduce(acc += z)
           end
       end
       acc
234462500
```

## 注意事項

名前の「非決定論的」は、削減の結果が決定論的ではない（すなわち、スケジュール依存）ことを示しています。*もし*削減関数が近似的に結合的である場合（例：浮動小数点数の`+`）、そうなります。厳密に結合的な操作（例："`vcat`"）を使用する計算（例：`Folds.collect`）では、結果はJuliaランタイムの特定のスケジューリング決定に依存しません。より具体的には、このエグゼキュータは決定論的な分割統治「タスク」グラフを生成しないスケジューリングを使用します。代わりに、グラフの形状は実行時の各計算の特定のタイミングによって決まります。

## キーワード引数

  * `basesize`: 基本ケースのサイズ。
  * `ntasks`: このエグゼキュータによって使用されるタスクの数。
  * `simd`: `false`、`true`、`:ivdep`、またはそれらのいずれかの`Val`。`true`または`:ivdep`の場合、各基本ケースの最も内側のループは`@simd`/`@simd ivdep`で注釈されます。`false`（デフォルト）の場合は通常のループを使用してください。
