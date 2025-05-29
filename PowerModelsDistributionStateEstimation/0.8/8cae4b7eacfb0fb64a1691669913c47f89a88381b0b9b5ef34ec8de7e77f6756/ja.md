```
add_measurements!(data::Dict, meas_file::String; actual_meas::Bool = false, seed::Int=0)
```

別のCSVファイルから測定データをPowerModelsDistributionデータ辞書に追加します。この関数がどのように機能するかを完全に理解するためには、最初にCSV測定ファイル形式を説明するドキュメントセクションを読むことをお勧めします。

# 引数

  * `data`: PowerModelsDistributionで使用可能な形式の数学的データ辞書
  * `meas_file`: 測定データを含むファイルのパスと名前
  * `actual_meas`: デフォルトはfalse。非正規分布に適用される場合、効果は`true`のものに上書きされます。正規分布の場合、以下が適用されます：

      * `false`: meas*fileの"par*1"は実際の測定値ではなく、例えば、誤差のないパワーフロー結果です。次に、与えられた正規分布から誤差を持つ値を抽出して偽の測定値が構築されます。
      * `true`: meas*fileの"par*1"の値は実際の測定値であり、"par_2"は測定の分布のσです。これらはさらなる処理なしに状態推定器の入力として直接使用されます。
      * CSVファイルに"parse"列が存在する場合、`true`または`false`は各個別の行（すなわち、測定）に関連付けられ、add*measurements!()自体のactual*meas入力を上書きします。
  * `seed`: 結果を再現可能にし、確率分布から誤差を持つ測定をサンプリングする際に異なるモンテカルロシナリオを探索するためのランダムシード値。
