```
MMI.predict(conf_model::JackknifePlusAbMinMaxRegressor, fitresult, Xnew)
```

For the [`JackknifePlusAbMinMaxRegressor`](@ref) 予測区間は次のように計算されます、

$$
\hat{C}_{n,\alpha}^{J+MinMax}(X_{n+1}) = \left[ \min_{i=1,...,n} \hat\mu_{-i}(X_{n+1}) -  \hat{q}_{n, \alpha}^{+} \{S_i^{\text{J+MinMax}} \}, \max_{i=1,...,n} \hat\mu_{-i}(X_{n+1}) + \hat{q}_{n, \alpha}^{+} \{S_i^{\text{J+MinMax}}\} \right] ,  i \in \mathcal{D}_{\text{train}}
$$

ここで、$\hat\mu_{-i}$ は$i$番目の点を除いたトレーニングデータにフィットしたモデルを示します。ジャックナイフ+ab-minmax手法は、[`JackknifePlusAbRegressor`](@ref) よりも保守的です。
