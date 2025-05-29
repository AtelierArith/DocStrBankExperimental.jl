```
DebugEntryChange{T} <: DebugAction
```

特定のエントリの変更を反復中に印刷します

# 追加フィールド

  * `print`:    (`print`) 結果を印刷するための関数
  * `prefix`:   (`"Change of :Iterate"`) 印刷出力のプレフィックス
  * `format`:   (`"$prefix %e"`) 印刷フォーマット（デフォルトで`prefix`を使用し、科学的表記法）
  * `field`:    [`AbstractManoptSolverState`](@ref) 内でアクセスできるフィールドのシンボル
  * `distance`: 2つのエントリの値の間の変更/距離を計算する関数 (p,o,x1,x2)
  * `storage`:  前の値 `:f` を保存するための [`StoreStateAction`](@ref)

# コンストラクタ

```
DebugEntryChange(f,d)
```

# キーワード引数

  * `io`:             (`stdout`) `IOStream`
  * `prefix`:         (`"Change of $f"`)
  * `storage`:        (`StoreStateAction((f,))`) [`StoreStateAction`](@ref)
  * `initial_value`: `o.field` の変更の初期値。
  * `format`:         (`"$prefix %e"`) 変更を印刷するためのフォーマット
