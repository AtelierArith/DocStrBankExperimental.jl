```
v_zero = reinit(instantiatedModel, _x, j, v_new, _leqMode; v_threshold=0.01)
```

状態 j を v*new で再初期化します。つまり、x[i] = v*new を設定します。ここで、i = instantiatedModel.equationInfo.x*info[j].startIndex です。もし v*new <= v*threshold の場合、x[i] をゼロに最も近い浮動小数点数に設定し、x[i] > 0 となるようにし、v*zero = true を返します。そうでなければ、v_zero = false を返します。

イベントフェーズ中に関数が呼び出されない場合や、leqMode >= 0 の場合（これは、線形方程式系を解くための for ループ内で reinit が呼び出されることを意味します - これはまだサポートされていません）にエラーが発生します。

# 実装ノート

getDerivatives!(..) の最初で、*x の適切な変数への代入が行われます。したがって、その後に reinit を介して _x[i] を設定しても、このモデル評価には即座の効果はありません。reinit では、instantiatedModel.eventHandler.newEventIteration = true が設定され、新しいイベント反復を強制します。次のイベント反復では、新しい値 v*new が _x からコピーされ、そのため効果が生じます。
