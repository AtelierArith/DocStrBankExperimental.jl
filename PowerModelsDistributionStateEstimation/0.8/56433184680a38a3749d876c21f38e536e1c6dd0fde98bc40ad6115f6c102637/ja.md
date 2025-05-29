```
reduce_single_phase_loadbuses!(data::Dict; exclude = [])
```

接続された負荷が1つのアクティブフェーズのみを持つ負荷バスの電圧変数の次元を削減します。

```
- data: ネットワークの`MATHEMATICAL`データモデル
- exclude: この変換が適用されないバス
```
