エネルギー評価は、String/NEB型メソッドにおいて、'serial'方式または'palindrome'方式で行うことができます：

  * `serial` : 常に同じ方向にパスを進む。
  * `palindrome` : 各イテレーションの後に、パスに沿った画像のエネルギー計算の順序が逆転します。

### パラメータ：

  * `direction` : パスに沿った画像を進む順序
