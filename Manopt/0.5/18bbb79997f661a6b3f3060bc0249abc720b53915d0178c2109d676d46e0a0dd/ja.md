```
DebugEntryChange{T} <: DebugAction
```

イテレーション中に特定のエントリの変更を印刷します

# 追加フィールド

  * `print`:    結果を印刷する関数
  * `prefix`:   印刷出力のプレフィックス
  * `format`:   印刷フォーマット（デフォルトで`prefix`と科学的表記を使用）
  * `field`:    [`AbstractManoptSolverState`](@ref)内でアクセスできるフィールドのシンボル
  * `distance`: エントリの2つの値の間の変更/距離を計算する関数 (p,o,x1,x2)
  * `storage`:  前の値`:f`を保存するための[`StoreStateAction`](@ref)

# コンストラクタ

```
DebugEntryChange(f,d)
```

## キーワード引数

  * `io=stdout`:                      デバッグに使用される`IOStream`
  * `prefix="Change of $f"`:          プレフィックス
  * `storage=StoreStateAction((f,))`:  [`StoreStateAction`](@ref)
  * `initial_value=NaN`:              `o.field`の変更の初期値。
  * `format="$prefix %e"`:            変更を印刷するためのフォーマット
