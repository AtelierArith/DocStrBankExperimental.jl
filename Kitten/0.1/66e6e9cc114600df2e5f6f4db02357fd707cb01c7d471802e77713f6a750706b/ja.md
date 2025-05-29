```
@cron(expression::String, name::String, func::Function)
```

このバリエーションは、登録された関数に手動で「名前」を付ける方法を提供します。この情報は、サーバーが起動時にすべてのcronジョブをログに記録するために使用されます。
