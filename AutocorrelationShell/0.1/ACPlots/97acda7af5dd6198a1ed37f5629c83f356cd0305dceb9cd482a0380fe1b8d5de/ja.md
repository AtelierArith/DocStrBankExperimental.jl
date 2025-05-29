```
wiggle!(wav; taxis=1:size(wav,1), zaxis=1:size(wav,2), sc=1, EdgeColor=:black, FaceColor=:black, Orient=:across, Overlap=true, ZDir=:normal)
```

現在表示されているグラフィックスにシェーディングされたウィグルのセットをプロットします

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

Nicholas Hauschによる翻訳 – Naoki Saito提供のMATLABファイル 前のMATLABバージョンの貢献者は、Anthony K. Booer (SLB) と Bradley Marchand (NSWC-PC) です。 Naoki Saitoによって改訂、2018年2月5日
