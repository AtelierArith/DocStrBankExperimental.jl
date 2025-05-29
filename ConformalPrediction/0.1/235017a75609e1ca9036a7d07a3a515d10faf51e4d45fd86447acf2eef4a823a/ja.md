```
MMI.predict(conf_model::JackknifeRegressor, fitresult, Xnew)
```

For the [`JackknifeRegressor`](@ref) 予測区間は次のように計算されます、

$$
\hat{C}_{n,\alpha}(X_{n+1}) = \hat\mu(X_{n+1}) \pm \hat{q}_{n, \alpha}^{+} \{S_i^{\text{LOO}}\}, \ i \in \mathcal{D}_{\text{train}}
$$

ここで、$S_i^{\text{LOO}}$ は、[`fit(conf_model::JackknifeRegressor, verbosity, X, y)`](@ref) で説明されているように生成される非適合性を示します。ジャックナイフ手法は、[`NaiveRegressor`](@ref) に関連する過剰適合の問題に対処します。
