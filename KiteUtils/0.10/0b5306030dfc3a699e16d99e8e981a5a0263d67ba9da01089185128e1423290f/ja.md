```
save_log(flight_log::SysLog, compress=true; path="")
```

SysLog型のフライトログを.arrowファイルとして保存します。デフォルトではlz4圧縮が使用されますが、2番目のパラメータに**false**を使用すると圧縮は使用されません。
