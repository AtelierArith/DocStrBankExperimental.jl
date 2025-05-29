```
preimage(f::ACSetTransformation,Y::StructACSet)
```

逆 f (A から B への) は、B の部分対象から A の部分対象への写像として定義されます。ACSet を部分対象にキャストしますが、前像を計算する際には自明な答えになります (必然的に A の最上位部分対象です)。
