```
@pddltheory module M ... end
```

は、PDDL理論としてモジュール `M` を宣言します。これにより、`M.@register`、`M.register!`、`M.deregister!` および `M.attach!` 関数が自動的に定義されます。
