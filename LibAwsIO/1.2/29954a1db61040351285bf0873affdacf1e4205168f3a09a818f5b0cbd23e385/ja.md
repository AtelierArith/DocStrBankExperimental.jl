```
aws_pem_objects_init_from_file_path(pem_objects, allocator, filename)
```

ファイルからPEMデータをデコードし、オブジェクトを順次読み取り、それらをpem*objectsに追加します。読み取れないオブジェクトに遭遇した場合、それまでに読み取ったすべてのオブジェクトのリストが返されます。PEMからオブジェクトを読み取れない場合や、オブジェクトをBase64デコードできない場合は、AWS*ERROR*PEM*MALFORMEDが発生します。out*pem*objectsは[`aws_pem_object`](@ref)構造体を値として格納します。この関数はpem_objectsリストを初期化します。このコードは遅く、メモリを割り当てるため、速さやリソースに敏感な処理の途中で呼び出さないようにしてください。

### プロトタイプ

```c
int aws_pem_objects_init_from_file_path( struct aws_array_list *pem_objects, struct aws_allocator *allocator, const char *filename);
```
