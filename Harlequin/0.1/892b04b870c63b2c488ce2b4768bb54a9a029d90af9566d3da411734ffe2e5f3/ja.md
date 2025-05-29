```
update_scanning_strategy(sstr::ScanningStrategy)
```

`ScanningStrategy`オブジェクトの内部フィールドを更新します。コンストラクタを使用して作成された後に`ScanningStrategy`オブジェクトのフィールドのいずれかを変更した場合は、`time2pointing`、`time2pointing!`、`genpointings`、および`genpointings!`のいずれかの関数を使用する前にこの関数を呼び出してください。これらの関数は、更新する必要があるいくつかの内部パラメータに依存しています。

```julia
sstr = ScanningStrategy()
# ... use sstr ...

sstr.borespinang_rad *= 0.5
update_scanning_strategy(sstr)
```
