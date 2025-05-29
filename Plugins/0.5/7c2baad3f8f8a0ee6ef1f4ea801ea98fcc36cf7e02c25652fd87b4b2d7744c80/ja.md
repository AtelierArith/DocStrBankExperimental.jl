```
function hooklist(plugins, hookfn)
```

与えられたプラグインによってマージされた `hookfn` の実装に対して、高速でインライン可能な呼び出しを可能にする HookList を作成します。

プラグインの型 `TPlugin` がプラグイン内に見つかった場合、次のシグネチャに一致するメソッドがあると、結果の HookList で参照されます: `hookfn(::TPlugin, ...)`
