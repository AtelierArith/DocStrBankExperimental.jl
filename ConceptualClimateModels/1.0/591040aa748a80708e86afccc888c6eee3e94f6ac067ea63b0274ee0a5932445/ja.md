```
SigmoidProcess <: Process
SigmoidProcess(variable, driver; left, right, scale, reference)
```

`variable`が`driver`変数に対してシグモイド依存性を持つ場合の一般的なプロセスです。残りの入力引数は実数または`@parameter`名付きパラメータである必要があります。

このプロセスは`tanh`関数に基づいてシグモイド関係を作成します：

```
variable ~ left + (right - left)*(1 + tanh(2(driver - reference)/scale))*0.5
```

つまり、`driver`が`reference`を中心に`scale`の範囲で増加するにつれて、変数は値`left`から値`right`に移行します。`reference`の代わりに`start`または`finish`キーワードを提供することができ、これにより`reference = start + scale/2`または`reference = finish - scale/2`になります。

式のパラメータに与えられた値が実数である場合、それらは`variable`の名前、次に`driver`の名前、そしてそれぞれ`_sigmoid_left`、`_sigmoid_right`、`_sigmoid_rate`、`_sigmoid_ref`で接頭辞が付けられた名付きパラメータになります。名前を変更したくないパラメータには`LiteralParameter`を使用してください。
