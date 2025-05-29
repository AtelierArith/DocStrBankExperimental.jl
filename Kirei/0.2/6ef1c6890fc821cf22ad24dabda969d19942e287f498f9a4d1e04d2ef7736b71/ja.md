```
@target [os=(windows, linux, macos)] [arch=(x86_64, aarch64, ...)] expr
```

ターゲットOSとアーキテクチャが指定された条件に一致する場合のみ、`expr`を評価します。

これは、条件をパース時に評価するために`@static`を使用します。
