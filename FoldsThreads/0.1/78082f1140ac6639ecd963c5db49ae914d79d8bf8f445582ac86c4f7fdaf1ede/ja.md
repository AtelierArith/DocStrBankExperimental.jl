```
DepthFirstEx(; [simd,] [basesize])
```

並列実行のための深さ優先スケジューリング。`findfirst`型の計算に便利です。

# 例

```jldoctest DepthFirstEx
julia> using FoldsThreads
       using Folds

julia> Folds.sum(i -> gcd(i, 42), 1:1000_000, DepthFirstEx())
4642844
```

# 拡張ヘルプ

`DepthFirstEx`は、入力コレクションに現れる順序で、サイズがほぼ`basesize`に等しいチャンクをスケジュールします。ただし、基本ケースの計算はすべてのタスクがスケジュールされるのを待ちません。このアプローチは、すべてのタスクが一度にスケジュールされてから還元が始まるよりもパフォーマンスが向上します。`DepthFirstEx`は、早期に終了できる還元（例：`findfirst`、`@floop`と`break`）に便利です。

## さらなる例

```jldoctest DepthFirstEx
julia> using FoldsThreads
       using FLoops

julia> @floop DepthFirstEx() for x in 1:1000_000
           y = gcd(x, 42)
           @reduce(acc += y)
       end
       acc
4642844
```

## キーワード引数

  * `basesize`: 基本ケースのサイズ。
  * `simd`: `false`、`true`、`:ivdep`、またはそれらのいずれかの`Val`。`true`または`:ivdep`の場合、各基本ケースの最も内側のループは`@simd`/`@simd ivdep`で注釈されます。`false`（デフォルト）の場合は通常のループを使用してください。
