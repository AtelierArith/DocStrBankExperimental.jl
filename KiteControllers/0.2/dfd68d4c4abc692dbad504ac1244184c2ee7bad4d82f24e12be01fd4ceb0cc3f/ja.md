FlightPathControllerは、Uwe Fechnerの博士論文の第6章に指定されています。

主な入力は、次の関数への呼び出しです：

  * on*control*command()
  * on*est*sys_state()

主な出力は、メソッドによって返される操縦値u_sです：

  * calc_steering()

時間ステップごとに、メソッド

  * on_timer

を呼び出す必要があります。

詳細については、docs/flight*path*controller*I.png、docs/flight*path*controller*II.png、およびdocs/flight*path*controller_III.pngを参照してください。
