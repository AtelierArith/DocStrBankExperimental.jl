非ブロッキングのイベントポーリング。キューに`Event`が追加されていなくても、クライアントイベントが消費されたかどうかを返す必要があります。

```julia
poll_for_events!(queue::WindowAbstractions.EventQueue)

```
