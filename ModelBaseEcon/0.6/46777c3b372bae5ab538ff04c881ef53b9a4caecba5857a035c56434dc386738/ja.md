```
issssolved(sstate::SteadyStateData)
```

定常状態が解かれた場合は `true` を返し、そうでない場合は `false` を返します。

!!! note
    この関数は、定常状態が解かれたとマークされているかどうかのみを確認します。保存された定常状態の値が実際に定常状態の方程式系を満たしているかどうかは検証しません。そのためには、StateSpaceEcon の `check_sstate` を使用してください。

