```
sticktask()
```

これは、Sense HATのジョイスティックが操作されると`StickEvent`を生成する`Task`です。新しい`StickEvent`が発生するまでブロックします。典型的な使用法は、新しいタスクを作成し、これを非同期に呼び出すことです。例えば、以下は各イベントに対して関数`f(::StickEvent)`を呼び出します：

```
@schedule for e in sticktask()
    f(e)
end
```
