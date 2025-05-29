$$
P = \begin{bmatrix}
P_{A, A} & P_{A, C} & P_{A, G} & P_{A, T} \\
P_{C, A} & P_{C, C} & P_{C, G} & P_{C, T} \\
P_{G, A} & P_{G, C} & P_{G, G} & P_{G, T} \\
P_{T, A} & P_{T, C} & P_{T, G} & P_{T, T} \end{bmatrix}
$$

指定された時間のために`NucleicAcidSubstitutionModel`のP行列を生成します。

呼び出し方は次のいずれかです。

1. `P(model, t)`、または
2. `P(model, t, bool)`

形式(2)は、bool=trueの場合にスケーリングされたQ行列から確率を取得します。スケーリングされたP行列から推定された枝の長さは、サイトあたりの期待される置換の数の単位です。`P(model, t, false)`は`P(model, t)`と同等です。
