```
wiggle(wav; taxis=1:size(wav,1), zaxis=1:size(wav,2), sc=1, EdgeColor=:black, FaceColor=:black, Orient=:across, Overlap=true, ZDir=:normal)
```

シェーディングされたウィグルのセットをプロットします

# 引数

  * `wav::Array`: 波形列の行列。
  * `taxis::Array=1:size(wav,1)`: 時間軸ベクトル
  * `zaxis::Array=1:size(wav,2)`: 空間軸ベクトル
  * `sc::Float=1`: スケールファクター/拡大率。
  * `EdgeColor::Symbol=:black`: ウィグルのエッジの色を設定します。
  * `FaceColor::Symbol=:black`: ウィグルのシェーディング色を設定します。
  * `Overlap::bool=true`: 信号のスケーリング方法。       true  - 信号が重なる（デフォルト）；       false - 信号が重ならないようにスケーリングされます。
  * `Orient::Symbol=:across`: ウィグルの向きを制御します。       :across - 左から右へ       :down   - 上から下へ
  * `ZDir::Symbol=:normal`: 空間軸の方向。       :normal  - 最初の信号が下（デフォルト）       :reverse - 最初の信号が上。

翻訳者: ニコラス・ハウシュ – MATLABファイル提供者: 斉藤直樹 前のMATLABバージョンの貢献者:  アンソニー・K・ブーア（SLB）およびブラッドリー・マーチャン（NSWC-PC） 改訂者: 斉藤直樹, 2018年2月5日
