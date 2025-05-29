```
simulation(seq::AbstractSequence, tr::Vector{Trajectory}, image::Array{T,3}
                ; opName="fast", r1map=[], r2map=[], fmap=[], senseMaps=[]
                , verbose=true, kargs...) where T<:Complex{<:AbstractFloat}
```

パルスシーケンスのすべてのエコーのk空間データをシミュレートします。エコーの強度はEPG形式を使用してシミュレートされます。フーリエ積分は正確に評価することも、NFFTを使用して評価することもできます。

...

# 引数

  * `seq::AbstractSequence`      - パルスシーケンス
  * `tr::Vector{Trajectory}`     - すべてのコントラストのための軌道
  * `image::Array{T,3}` - 変換される画像
  * (`r1map=[]`)                 - オブジェクトのR1マップ（実数）
  * (`r2map=[]`)                 - オブジェクトのR2マップ（実数） / （GREシーケンスのためのR2*）
  * (`fmap=[]`)                  - フィールドマップ（実数）
  * (`opName="fast")             - 使用する演算子の名前（"explicit"または"fast"）
  * (`sensmaps=[]`)              - コイル感度の配列
  * (`verbose=true`)             - trueの場合、進行状況を表示
  * `kargs...`                   - 追加のキーワード引数

...
