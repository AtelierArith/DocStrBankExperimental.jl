````
jlocalframe(f, [returntype]; [capacity = 16])

Manages java local references by using JNI's PushLocalFrame and PopLocalFrame.
Only the local reference returned by f will be valid. Other local references
will be freed and available for garbage collection.

Specifying a `returntype` will allow for type stability. If `returntype` is
specified and is not `Nothing` or `Any`, it will also be passed to the function.

Capacity specifies the minimum number of local references that can be
created. See the [JNI documentation](
https://docs.oracle.com/en/java/javase/15/docs/specs/jni/functions.html#pushlocalframe
)
for further information.

# Example
```
julia> jlocalframe() do
           a = JObject() # Local reference created, will be GCed
           println(a)
           b = JObject() # Local reference returned
           println(b)
           b
       end

julia> jlocalframe(JObject) do T # Specify returntype for type stability
           a = T()
           println(a)
           b = T()
           println(b)
           b
       end

julia> jlocalframe(Nothing) do # Specify Nothing if you do want to return anything
           a = JObject()
           println(a)
       end
```
````
