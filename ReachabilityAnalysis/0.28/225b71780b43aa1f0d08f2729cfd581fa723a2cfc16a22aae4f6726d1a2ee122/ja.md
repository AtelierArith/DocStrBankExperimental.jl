```
TemplateReachSet{N, VN, TN<:AbstractDirections{N, VN}, SN<:AbstractVector{N}} <: AbstractLazyReachSet{N}
```

与えられた方向のセットにおけるセットのサポート関数を格納するリーチセット。

### 注意事項

この構造体には以下のパラメータがあります：

  * `N`  – 表現の数値型を指します。
  * `VN` – テンプレートのベクトル型を指します。
  * `TN` – テンプレート型を指します。
  * `SN` – サポート関数の評価を保持するベクトル型です。

`AbstractDirections`の具体的なサブタイプは`LazySets`ライブラリで定義されています。

このリーチセットは、方向のセットとサポート関数によってセットを暗黙的に表現します。 `set(R::TemplateReachSet)`は半空間表現のポリヘドロンを返します。

`AbstractReachSet`インターフェースから継承されたゲッタ関数に加えて、以下のメソッドが利用可能です：

  * `directions(R)`           – このリーチセットの面に対して法線となる方向のセットを返します
  * `support_functions(R)`    – サポート関数の評価のベクトルを返します
  * `support_functions(R, i)` – サポート関数の評価のベクトルの`i`-番目の座標を返します
