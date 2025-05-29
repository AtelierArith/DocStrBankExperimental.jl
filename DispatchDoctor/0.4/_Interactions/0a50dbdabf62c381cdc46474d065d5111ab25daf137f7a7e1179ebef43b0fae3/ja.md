```
register_macro!(macro_name::Symbol, behavior::MacroInteractions)
```

指定された動作でマクロを`MACRO_BEHAVIOR`リストに登録します。

この関数は、新しいマクロとその関連する動作を、安定化プロセス中に遭遇したときにマクロがどのように扱われるべきかを追跡するグローバルリストに追加します。動作は`CompatibleMacro`、`IncompatibleMacro`、または`DontPropagateMacro`のいずれかであり、`@stable`マクロが登録されたマクロとどのように相互作用するかに影響を与えます。

`@stable`のデフォルトの動作は、明示的に宣言されない限り`CompatibleMacro`と見なすことです。

# 引数

  * `macro_name::Symbol`: 登録するマクロを表すシンボル。
  * `behavior::MacroInteractions`: マクロに関連付ける動作で、どのように扱われるべきかを決定します。

# 例

```julia
using DispatchDoctor: register_macro!, IncompatibleMacro

register_macro!(Symbol("@mymacro"), IncompatibleMacro)
```
