XAIBaseにおけるすべての特徴選択器の抽象スーパタイプ。

特徴選択器は呼び出し可能であり、選択された各特徴に対して`CartesianIndices`のベクトルを返すことが期待されています。

## 注意

XAIBaseインターフェースは現在、特徴が2次元または4次元（`(features, batchsize)`または`(width, height, features, batchsize)`）であると仮定しています。

また、バッチ次元が特徴の最後の次元であると仮定しています。
