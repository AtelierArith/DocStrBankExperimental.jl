接続試行が完了したときに呼び出されます。

試行が失敗した場合、error*codeはゼロ以外の値になり、接続ポインタはNULLになります。また、[`aws*event*stream*rpc*client*on*connection*shutdown_fn`](@ref)は呼び出されません。

試行が成功した場合、error*codeは0になり、接続ポインタは有効です。ポインタのメモリが破棄されるのを防ぐために、[`aws*event*stream*rpc*client*connection*acquire`](@ref)()を呼び出す必要があります。接続ポインタの使用が完全に終了したら、[`aws*event*stream*rpc*client*connection*release`](@ref)()を呼び出さなければなりません。そうしないと、そのメモリがリークします。ネットワーク接続が閉じたときに、[`aws*event*stream*rpc*client*on*connection*shutdown*fn`](@ref)が呼び出されます。接続が終了している場合でも、まだオープンしている場合は、aws*aws*event*stream*rpc*client_close()を呼び出さなければなりません。そうしないと、ネットワーク接続はオープンのままとなり、release()を呼び出しても接続は閉じません。
