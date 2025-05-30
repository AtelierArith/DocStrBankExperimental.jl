```
update_exogenous!(ls::RigidBodyMotion,a_edof::AbstractVector)
```

`ls`の外因バッファを、供給された外因加速度ベクトル`a_edof`で変更します。この関数は、外部ループから積分器に時間変化する外因値を供給するのに便利です。
