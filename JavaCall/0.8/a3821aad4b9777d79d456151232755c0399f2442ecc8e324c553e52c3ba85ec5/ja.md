```
JavaLocalRefは、関数呼び出しのローカル変数と一緒に使用することを目的としたJavaRefです。
関数呼び出しの後、これらの参照は解放され、ガーベジコレクションされる可能性があります。以下のJNIメモリ管理に関する注意を参照してください。

これはJNIから返されるデフォルトの参照タイプです。

メモリ管理のためにJNI.PushLocalFrame / JNI.PopLocalFrameと一緒に使用してください。
また、JNI.EnsureLocalCapacityも参照してください。

内部ポインタはJNI.DeleteLocalRefを使用して削除する必要があります。
```
