```
ApproximatelyError{V,S} <: Exception
```

2つのデータ構造、例えば点や接ベクトルの間で発生するエラーを格納します。

# フィールド

  * `val` 2つの近似要素の間の距離 – これが不明な場合は `NaN` に設定されます
  * `msg` 実行されたテストと失敗の理由についての詳細を提供するメッセージ。

# コンストラクタ

```
ApproximatelyError(val::V, msg::S) where {V,S}
```

値 `val` とメッセージ `msg` を持つエラーを生成します。

```
ApproximatelyError(msg::S) where {S}
```

値なしでメッセージを生成します（内部的に `val=NaN` を使用）およびメッセージ `msg`。
