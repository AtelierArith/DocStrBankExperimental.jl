```
aws_secure_tunnel_state
```

セキュアトンネルが存在できるさまざまな状態。セキュアトンネルには現在の状態と望ましい状態の両方があります。望ましい状態は{STOPPED, CONNECTED, TERMINATED}のいずれかである必要があります。セキュアトンネルは、(1) 望ましい状態の変更、または (2) 外部イベントに基づいて状態を遷移します。

ほとんどの状態は中断可能ですが（望ましい状態の変更が即座に状態の変更を引き起こすという意味で）、CONNECTINGは非同期コールバック（キャンセルができない）を完了するのを待っているため、中断することはできません。
