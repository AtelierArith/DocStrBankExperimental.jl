```
Objective(logf::Function, support:)
Objective(logf::Function, grad::Function)
```

サンプリングされる目的関数を格納するための便利な構造体です。fの対数を受け取る必要があり、fを直接受け取ることはできません。デフォルトでは自動微分を使用しますが、ユーザーはオプションで導関数を提供することができます。
