```
@replaceparameterlinks model oldmodel => newmodel
```

この関数は、モデルが別のモデルオブジェクトにリンクするパラメータを使用している場合に使用されます。この関数は、Mainモジュールに表示されるモデルのペアで呼び出す必要があります。

これは、モデルがモジュール化され、サテライトモデルを含む場合に便利です。この関数を使用して、修正されたサテライトモデルのパラメータを修正されたメインモデルにリンクできます。たとえば、FRBUS_VARモデルにメインモデルとサテライトモデルがある場合、次のワークフローが理にかなっています。

```
using FRBUS_VAR
m = deepcopy(FRBUS_VAR.model)
m_sattelite = deepcopy(FRBUS_VAR.sattelitemodel)

## mに変更を挿入
@reinitialize m
@replaceparameterlinks m_sattelite FRBUS_VAR.model => m
@reinitialize m_sattelite

```

このような変更の後は、モデルに対して[`@reinitialize`](@ref)を呼び出す必要があります。
