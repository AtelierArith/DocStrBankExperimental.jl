```
debounce(dt, input, f=(acc,x)->x, init=value(input), reinit=x->x;
            typ=typeof(init), name=auto_name!(string("debounce ",dt,"s"), input))
```

`dt`秒が最後に`input`が更新されてから経過するまで、更新を遅延させる信号を作成します。デフォルトでは、デバウンス信号は、デバウンス信号が最後に更新されてからの`input`信号の最後の更新を保持します。

この動作は、`f`、`init`、および`reinit`引数によって変更できます。`init`および`f`関数は、`foldp`の`init`および`f`に似ています。`reinit`は、デバウンスが更新を送信した後に呼び出され、蓄積の初期値を再初期化します。1つの引数、前の蓄積値を受け取ります。

例えば、`y = debounce(0.2, x, push!, Int[], _->Int[])`は、整数信号`x`への更新のベクトルを蓄積し、`x`が非アクティブ（更新しない）で0.2秒間経過した後にプッシュします。
