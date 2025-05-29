```
set_approximation_mode(m::GMPModel, mode::AbstractApproximationMode)
```

mの近似モードをmodeに設定します。ソルバーによっては、プライマルまたはデュアルの定式化の方が効率的である場合があります。数値的な問題が発生した場合にモードを変更することも興味深いかもしれません。modeの可能な値は次のとおりです：

  * PRIMAL*RELAXATION*MODE()
  * DUAL*STRENGTHEN*MODE()（デフォルト）

```

```
