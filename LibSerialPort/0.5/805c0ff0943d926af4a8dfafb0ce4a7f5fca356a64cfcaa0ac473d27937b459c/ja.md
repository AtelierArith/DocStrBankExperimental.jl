```
set_flow_control(sp::SerialPort;
                 rts::SPrts = SP_RTS_OFF,
                 cts::SPcts = SP_CTS_IGNORE,
                 dtr::SPdtr = SP_DTR_OFF,
                 dst::SPdsr = SP_DSR_IGNORE,
                 xonxoff::SPXonXoff = SP_XONXOFF_DISABLED)`
```

フロー制御ラインとメソッドを設定します。多くのシステムはすべてのオプションをサポートしていません。サポートされていないオプションが要求された場合、ライブラリはSP*ERR*SUPPを返します。

  * `rts`は出力ライン*Ready To Send (RTS)*を制御し、`SP_RTS_OFF`（デフォルト）、`SP_RTS_ON`、および`SP_RTS_FLOW_CONTROL`の値を取ることができます。
  * `cts`は入力ライン*Clear To Send (CTS)*を制御し、`SP_CTS_IGNORE`（デフォルト）および`SP_CTS_FLOW_CONTROL`の値を取ることができます。
  * `dtr`は出力ライン*Data Terminal Ready (DTR)*を制御し、`SP_DTR_OFF`（デフォルト）、`SP_DTR_ON`、および`SP_DTR_FLOW_CONTROL`の値を取ることができます。
  * `dsr`は入力ライン*Data Set Ready (DSR)*を制御し、`SP_DSR_IGNORE`（デフォルト）および`SP_DSR_FLOW_CONTROL`の値を取ることができます。
  * `xonxoff`は制御バイトXOFF（送信を一時停止、0x13、Ctrl-S）およびXON（送信を再開、0x11、Ctrl-Q）を介した[ソフトウェアフロー制御](https://en.wikipedia.org/wiki/Software_flow_control)がアクティブであるかどうか、またその方向を制御します。値は`SP_XONXOFF_DISABLED`（デフォルト）、`SP_XONXOFF_IN`、`SP_XONXOFF_OUT`、および`SP_XONXOFF_INOUT`を取ることができます。
