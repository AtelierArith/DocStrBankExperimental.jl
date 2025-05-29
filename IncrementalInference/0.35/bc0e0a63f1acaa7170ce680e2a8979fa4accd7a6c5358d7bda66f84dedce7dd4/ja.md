```julia
getCliqMat(cliq; showmsg)

```

クリークの因子変数の関連性のブール行列を返します。オプションで、上向きメッセージのシングルトンを含めることができます（`showmsg::Bool=true`）。変数の順序は `getCliqAllVarIds` に対応しています。
