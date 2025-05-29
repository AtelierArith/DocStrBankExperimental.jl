```
destroy!(wallet::AbstractWallet, asset, quantity;
         fulfill_maximum=false, check, onfailure)
```

ウォレットに含まれている場合、指定された資産の一定量を破棄します。`fulfill_maximum`が`true`の場合、取引を可能な限り満たします。
