```
aws_websocket_release(websocket)
```

ウェブソケットの参照カウントを減少させます。参照カウントがゼロに達すると、接続はシャットダウンされます（まだシャットダウンされていない場合）。ユーザーは、ウェブソケットの使用が終わったらそれを解放する必要があります。この操作が行われるまで、ウェブソケットのメモリは再利用できません。この関数が呼び出された後もコールバックは続けて発火する可能性があり、「shutdown」が最終コールバックとなります。この関数は任意のスレッドから呼び出すことができます。

NULLを渡すことは安全であり、何も起こりません。

### プロトタイプ

```c
void aws_websocket_release(struct aws_websocket *websocket);
```
