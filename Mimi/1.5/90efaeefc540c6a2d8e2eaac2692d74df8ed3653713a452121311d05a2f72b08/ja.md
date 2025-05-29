```
defcomposite(cc_name, ex)
```

`cc_name`というMimi CompositeComponentDefを`ex`の式で定義します。式はすべて、より長いAPI呼び出しの省略形であり、以下を含みます。

```
p = Parameter(...)
v = Variable(varname)
local_name = Component(name)
Component(name)  # `name = Component(name)`と同等
connect(...)
```

変数名は、コンポーネントID（モジュールによってプレフィックスされる場合があります。例：`Mimi.adder`）の後に`.`とそのコンポーネント内の変数名が続く形で表現されます。したがって、形式は`modname.compname.varname`または`compname.varname`であり、現在のモジュールで知られている必要があります。

リーフコンポーネントとは異なり、コンポジットコンポーネントにはユーザー定義の`init`または`run_timestep`関数はありません。これらは内部で定義され、構成要素コンポーネントを反復処理し、それぞれの関連メソッドを呼び出します。
