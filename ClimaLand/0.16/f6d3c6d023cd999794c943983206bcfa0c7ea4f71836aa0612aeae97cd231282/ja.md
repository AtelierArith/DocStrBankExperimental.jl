```
boundary_vars(::AbstractBC, ::ClimaLand.BottomBoundary)
```

モデルの補助状態に追加する追加変数のシンボルのリストで、PDEを解くモデルの場合、デフォルトでは底面境界フラックスフィールドのストレージを追加しますが、使用される境界条件のタイプに応じて拡張できます。

PDEを解く土壌および土壌CO2モデルでは、傾向関数とupdate*boundary*fluxes関数がフィールド`:bottom_bc`にアクセスするようにコーディングされており、これがデフォルトとなっています。これがあなたの（PDE）モデルの望ましい動作でない場合は、新しいメソッドでこの関数を拡張できます。

フィールド`bottom_bc_wvec`は、割り当てを防ぐためだけに作成されており、傾向関数でのみ使用されます。

この関数は、`auxiliary_vars`を使用するのと全く同じ方法で使用してください。
