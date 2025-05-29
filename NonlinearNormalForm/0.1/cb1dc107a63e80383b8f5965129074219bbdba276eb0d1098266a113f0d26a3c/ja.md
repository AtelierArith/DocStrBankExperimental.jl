```
mul!(Q::Quaternion, Q1::Quaternion, Q2::Quaternion)
```

`Q`を`Q1*Q2`に等しく設定し、ゼロアロケーションで行います。`Q`は`Q1`または`Q2`のいずれともエイリアスされてはいけません。
