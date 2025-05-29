```
LLRRegularization
```

局所的低ランク（LLR）正則化のための近接写像を実装する正則化項で、特異値しきい値処理を使用します。

# 引数

  * `λ`                  - 正則化パラメータ

# キーワード

  * `shape::Tuple{Int}`            - 画像の次元
  * `blockSize::Tuple{Int}=(2,2)`  - 特異値しきい値処理を行うパッチのサイズ
  * `randshift::Bool=true`         - 平行移動不変性を確保するためにパッチをランダムにシフトする
  * `fullyOverlapping::Bool=false` - 完全に重なり合うブロックまたは重ならないブロックの選択
