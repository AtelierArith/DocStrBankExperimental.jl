```
struct MaxSizeBranchCount
```

結果の最大サイズとブランチの数を返します。

# フィールド

  * `size::Int`: 結果の最大サイズ。
  * `count::Int`: そのサイズのブランチの数。

# コンストラクタ

  * `MaxSizeBranchCount(size::Int)`: 指定されたサイズで `MaxSizeBranchCount` を作成し、カウントを 1 に初期化します。
  * `MaxSizeBranchCount(size::Int, count::Int)`: 指定されたサイズとカウントで `MaxSizeBranchCount` を作成します。
