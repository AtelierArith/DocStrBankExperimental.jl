```
MassProp(m, Ixx, Iyy, Izz, Ixz, Ixy, Iyz)
```

質量と慣性モーメントはボディフレーム内で定義されます。 Ixx = int(y^2 + z^2, dm) Ixz = int(xz, dm)

ほとんどの航空機はy軸について対称であるため、非ゼロ成分のみを指定するための便利なメソッドがあります。 MassProp(m, Ixx, Iyy, Izz, Ixz)
