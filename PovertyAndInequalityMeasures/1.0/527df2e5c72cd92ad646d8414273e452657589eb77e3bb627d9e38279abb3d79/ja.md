貧困指標の辞書を作成します。

これは、HaughtonとKhandkerによる[世界銀行の貧困ハンドブック](http://documents.worldbank.org/curated/en/488081468157174849/Handbook-on-poverty-and-inequality)に基づいています。

引数：

  * `rawdata` - 実数のnxm配列; 各行は観察値; 1つの列は重み、もう1つは収入である必要があります; 重みと収入の位置は、指定されていない限り1と2であると仮定されます
  * `line` - 貧困ライン、すべての観察に対して同じと仮定されます（したがって、収入はすでに等価化されていると仮定されます）
  * `foster_greer_thorndyke_alphas` - FGT貧困指標の係数; FGT(0)はヘッドカウントに対応し、FGT(1)はギャップに対応します; カウントとギャップは直接計算されますが、互いに確認する価値があります。
  * `growth`は（例えば）0.01で、期間ごとの1%を示し、「退出までの時間」指標に使用されます。

出力は、各指標のエントリを持つ辞書です。

指標は次のとおりです：

  * `headcount`;
  * `gap`;
  * `Foster Greer Thorndyke`、`foster_greer_thorndyke_alphas`の各値について;
  * `Watts`;
  * 指定された成長率に対する`time to exit`;
  * `Shorrocks`;
  * `Sen`。

世界銀行、章4を参照してください。
