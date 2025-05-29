```
update_exogenous!(ls::RigidBodyMotion,a_edof::AbstractVector)
```

`ls`の外因性バッファを、供給された外因性加速度ベクトル`a_edof`で変更します。この関数は、外部ループから積分器に時間変化する外因性値を供給するのに便利です。
