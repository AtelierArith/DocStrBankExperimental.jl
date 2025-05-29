ヘルパー関数は、ファクターグラフ内の複数の `Pose2AprilTag4Corners` ファクターのデコンボリューション予測と指定された測定値との間の不一致を示す集約コストを生成および計算します。

アイデアは、悪いキャリブレーションが何らかのSLAM結果をもたらし、十分な情報があれば、そのSLAM結果を使用して、AprilTagの視認をキャプチャするために使用されたカメラのより良いキャリブレーション推定をブートストラップできるということです。この関数は、通常の解が見つかった後にファクターグラフの目的内でその二次パラメータ検索を助けることを目的としています。

ノート

  * `pred, _ = approxDeconv(dfg, fct)`
  * `fct.preimage[1](pred[:,idx], [f_width, f_height, c_width, c_height, taglength])`

      * `fct.preimage[1]` はプレイメージを見つけるための関数です。
  * `obj = (fc_wh) -> fct.preimage[1](pred[:,idx], fc_wh)`

      * `fc_wh = [f_width, f_height, c_width, c_height, 0.172]`
  * `obj2 = (fcwh) -> obj([fcwh[1]; fcwh[1]; fcwh[2]; c_height; taglength])`
  * `result = Optim.optimize(obj, fct.preimage[2], BFGS(), Optim.options(x_tol=1e-8))`

      * 最適化のための保存された初期推定 `fct.preimage[2]`
