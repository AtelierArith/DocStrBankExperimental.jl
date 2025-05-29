```
send!(source::AbstractWallet, target, asset, quantity;
      fulfill_maximum=false, check, onfailure)
```

指定された資産の一定量を、元のウォレットにこの量が含まれている場合にターゲットに送信します。`fulfill_maximum`が`true`の場合、取引を可能な限り満たします。
