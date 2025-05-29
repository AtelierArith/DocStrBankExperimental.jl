````
jlocalframe(f, [returntype]; [capacity = 16])

JNIのPushLocalFrameとPopLocalFrameを使用して、Javaのローカル参照を管理します。
fによって返されるローカル参照のみが有効になります。他のローカル参照は解放され、ガーベジコレクションの対象となります。

`returntype`を指定すると、型の安定性が得られます。`returntype`が指定され、`Nothing`または`Any`でない場合、それも関数に渡されます。

Capacityは、作成できるローカル参照の最小数を指定します。詳細については、[JNI documentation](
https://docs.oracle.com/en/java/javase/15/docs/specs/jni/functions.html#pushlocalframe
)を参照してください。

# 例
```
julia> jlocalframe() do
           a = JObject() # ローカル参照が作成され、GCされる
           println(a)
           b = JObject() # ローカル参照が返される
           println(b)
           b
       end

julia> jlocalframe(JObject) do T # 型の安定性のためにreturntypeを指定
           a = T()
           println(a)
           b = T()
           println(b)
           b
       end

julia> jlocalframe(Nothing) do # 何も返したくない場合はNothingを指定
           a = JObject()
           println(a)
       end
```
````
