```
energy(sys::System; charges=Float64[], dipoles=Vec3[])
```

周期的な `charges` と `dipoles` のシステムに対する Ewald エネルギーを $1/4\pi\epsilon_0$ の単位で計算します。もしチャージまたは双極子のパラメータが省略された場合、それらはゼロと見なされます。隣接リストもオプションで提供できます。詳細についてはソースコードを参照してください。
