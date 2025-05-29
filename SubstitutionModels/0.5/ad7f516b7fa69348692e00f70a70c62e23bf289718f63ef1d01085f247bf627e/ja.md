`NucleicAcidSubstitutionModel`のためのQ行列を生成します。形式は次の通りです：

$$
Q = \begin{bmatrix}
Q_{A, A} & Q_{A, C} & Q_{A, G} & Q_{A, T} \\
Q_{C, A} & Q_{C, C} & Q_{C, G} & Q_{C, T} \\
Q_{G, A} & Q_{G, C} & Q_{G, G} & Q_{G, T} \\
Q_{T, A} & Q_{T, C} & Q_{T, G} & Q_{T, T} \end{bmatrix}
$$

次のように呼び出します：

1. `Q(model)`、または
2. `Q(model, bool)`

形式(2)は、$_π(model) ⋅ -diag(Q(model)) = 1$ となるように行列をスケーリングします。`Q(model, false)`は`Q(model)`と同等です。
