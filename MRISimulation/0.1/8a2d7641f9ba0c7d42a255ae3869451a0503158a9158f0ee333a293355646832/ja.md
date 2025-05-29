```
simulation(tr::Trajectory, image::Array{T}, correctionMap = []; opName="fast"
          , senseMaps=[], verbose=true, kargs...) where T<:Complex{<:AbstractFloat}
```

与えられた画像をk空間ドメインに変換します。軌道が2Dか3Dかをディスパッチします。フーリエ積分は正確に評価することも、NFFTを使用して評価することもできます。デモジュレートされた信号を返します。

...

# 引数

  * `tr::Trajectory`             - 三次元の軌道
  * `image::Array{T,3}` - 変換される画像
  * (`correctionMap=[]`)         - 磁場のオフレゾナンス（虚数）マップと緩和マップ（実数）の合計
  * (`opName="fast")             - 使用する演算子の名前（"explicit"または"fast"）
  * (`sensmaps=[]`)              - コイル感度の配列
  * (`verbose=true`)             - trueの場合、進行状況を印刷します
  * `kargs...`                   - 追加のキーワード引数

...
