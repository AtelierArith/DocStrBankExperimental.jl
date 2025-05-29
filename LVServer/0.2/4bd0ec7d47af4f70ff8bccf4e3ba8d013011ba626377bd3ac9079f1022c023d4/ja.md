```
setglobals(;isOK, extant=scriptexists, excpn = nothing)
```

`LVServer` モジュールのグローバル変数を設定します。デフォルトでは `scriptexists` の値を変更しないでください。この関数は、トップレベルのスクリプトから使用します。例えば、LabVIEW から実行する場合です。

# 例

```julia-repl

julia> setglobals(;isOK=true, extant=true);

```
