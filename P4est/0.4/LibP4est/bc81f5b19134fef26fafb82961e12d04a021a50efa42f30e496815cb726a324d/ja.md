sharers配列に格納されている構造。

shared*nodesは、ローカルノードにインデックスを付ける[`p4est*locidx*t`](@ref)のソートされた配列です。shared*nodes配列には、現在のランクが所有するノードの連続した（または空の）セクションがあります。shared*mine*offsetとshared*mine*countは、ローカルノード配列ではなくshared*nodes配列をインデックス付けすることによってこのセクションを特定します。owned*offsetとowned*countは、リストされたランクが所有するローカルノードのセクションを定義します（セクションは空である可能性があります）。現在のプロセスにとって、これらは[`p8est*lnodes_t`](@ref)のものと一致します。
