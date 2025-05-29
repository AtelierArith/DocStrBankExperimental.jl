```
intersection([f], g₁, g₂)
```

2つのジオメトリまたはドメイン `g₁` と `g₂` の交差を計算し、それに関数 `f` を適用します。デフォルトの関数は `identity` です。

## 例

```julia
intersection(g₁, g₂) do I
  if I isa CrossingLines
    # 何かをする
  else
    # 何もしない
  end
end
```

### 注意事項

カスタム関数 `f` を使用して戻り値の型の数を減らすと、Julia はコードの分岐を最適化し、特化したコードを生成することができます。これは `f === identity` の場合には当てはまりません。
