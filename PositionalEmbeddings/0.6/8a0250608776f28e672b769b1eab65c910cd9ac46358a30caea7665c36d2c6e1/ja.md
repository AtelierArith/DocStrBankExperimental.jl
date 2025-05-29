```
RoPE(head_size::Int, seq_len::Int;
    base::Number=10_000,
    scale::Number=1.0)
```

ロタリー位置埋め込み (RoPE) の実装は、論文「RoFormer: Enhanced Transformer with Rotary Position Embedding」に記載されています。

次の引数を使用して RoPE オブジェクトを構築します：

  * `head_size::Int`: 回転を適用するヘッドサイズ（2の倍数である必要があります）
  * `seq_len::Int`: サポートする最大シーケンス長
  * `base::Number=10_000`: 周波数の幾何級数の基数
  * `scale::Number=1.0`: 周波数のスケーリングファクター

# 例

```julia
# ヘッドサイズ 512 および最大シーケンス長 1024 のモデル用に RoPE を作成
rope = RoPE(512, 1024)

# 入力テンソル (head_size, seq_len, nheads*batch_size) に RoPE を適用
Q = randn(Float32, 512, 100, 32)
Q_positioned = rope(x)
```
