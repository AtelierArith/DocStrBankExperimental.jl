```
FresnelInterface{T} <: OpticalInterface{T}
```

二つの材料の間のインターフェースで、[フレネル方程式](https://en.wikipedia.org/wiki/Fresnel_equations)に従って定義された挙動を持ち、指定された反射率と透過率を持ちます。偏光のない光を仮定します。

```julia
FresnelInterface{T}(insidematerial, outsidematerial; reflectance = 0, transmission = 1, interfacemode = ReflectOrTransmit)
```

interfacemodeは、光線を決定論的に追跡するために使用できます。有効な値はInterfaceMode列挙型で定義されています。Reflectはすべての値が反射されることを意味し、Transmitはすべての値が透過されることを意味します。ReflectOrTransmitは、反射率と透過率の引数によって与えられる分布で光線をランダムに反射および透過します。これがデフォルトでもあります。すべての場合において、光線と共に記録されたパワーは正しく更新されます。これは、連続的なレイトレーシングを擬似的に行うために使用できます。たとえば、ビームスプリッターの表面は、二つの出射光線経路の間で切り替えるために、ReflectまたはTransmitに設定できます。
