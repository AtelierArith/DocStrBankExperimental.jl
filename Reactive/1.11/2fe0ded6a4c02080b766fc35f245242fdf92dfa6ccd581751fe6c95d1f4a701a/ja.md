```
throttle(dt, input, f=(acc,x)->x, init=value(input), reinit=x->x;
            typ=typeof(init), name=auto_name!(string("throttle ",dt,"s"), input), leading=false)
```

信号を制御して、最大で毎dt秒ごとに更新します。デフォルトでは、制御された信号は各dt秒の時間ウィンドウ内で`input`信号の最後の更新を保持します。

この動作は、`f`、`init`、および`reinit`引数によって変更できます。`init`および`f`関数は、`foldp`の`init`および`f`に似ています。`reinit`は新しい制御時間ウィンドウが開くときに呼び出され、蓄積の初期値を再初期化します。これは、前の蓄積値という1つの引数を受け取ります。

例えば、`y = throttle(0.2, x, push!, Int[], _->Int[])`は、0.2秒の時間ウィンドウ内で発生する整数信号`x`への更新のベクトルを作成します。

`leading`が`true`の場合、`input`からの最初の更新は制御信号によって即座に送信されます。`false`の場合、最初の更新は`input`の最初の更新から`dt`秒後に発生します。

v0.4.1の新機能：`throttle`の以前のバージョンからの動作は、現在`debounce`信号タイプで利用可能です。
