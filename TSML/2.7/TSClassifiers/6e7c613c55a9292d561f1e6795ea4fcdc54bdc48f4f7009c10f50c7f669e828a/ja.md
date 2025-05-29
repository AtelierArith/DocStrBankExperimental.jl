```
TSClassifier(
   Dict(
      # トレーニングディレクトリ
      :trdirectory => "",
      :tstdirectory => "",
      :modeldirectory => "",
      :feature_range => 7:20,
      :juliarfmodelname => "juliarfmodel.serialized",
      # 出力するクラス
      # (:class).
      :output => :class,
      # この実装に特有のオプション。
      :impl_args => Dict(
         # 純度閾値 CombineMLd 以上の葉をマージする。
         :purity_threshold => 1.0,
         # 決定木の最大深さ（デフォルト：最大なし）。
         :max_depth => -1,
         # 各葉が持つ必要がある最小サンプル数。
         :min_samples_leaf => 1,
         # 分割に必要な最小サンプル数。
         :min_samples_split => 2,
         # 分割に必要な最小純度の増加。
         :min_purity_increase => 0.0
      )
   )
)
```

与えられた特定のタイプの時系列の集まり。各時系列の統計的特徴を取得し、これらをRF分類器への入力として使用し、出力をTSタイプとしてトレーニングおよびテストします。別のオプションは、これらの統計的特徴をクラスタリングに使用し、クラスタの質を確認することです。精度が低い場合は、さらに統計的特徴を追加し、トレーニングとテストのために概説された同じプロセスを繰り返します。各時系列は、そのタイプに基づいて名前が付けられ、ターゲット出力として使用されると仮定します。たとえば、温度の時系列はtemperature?.csvという名前になり、?は整数です。ディレクトリ内の各ファイルをループし、統計を取得して辞書/データフレームに記録し、トレーニング/テストを行います。デフォルトでは、データタイプの分類にRandomForestを使用します。
