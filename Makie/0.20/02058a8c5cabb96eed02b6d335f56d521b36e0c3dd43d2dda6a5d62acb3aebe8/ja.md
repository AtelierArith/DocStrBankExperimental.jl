```
PointLight(color, position[, attenuation = Vec2f(0)])
PointLight(color, position, range::Real)
```

指定された`position`に配置された点状の光源で、指定された光の`color`を持ちます。

オプションで、減衰パラメータを使用して距離に応じて光源の明るさを減少させることができます。減少は`1 / (1 + attenuation[1] * distance + attenuation[2] * distance^2)`で与えられます。あるいは、光の`range`を渡して一致するデフォルトの減衰パラメータを生成することもできます。満足のいく結果を得るためには、光の強度、つまり光の色を1より大きい値に設定する必要があることに注意してください。

利用可能性：

  * `shading = MultiLightShading`を使用したGLMakie
  * RPRMakie
