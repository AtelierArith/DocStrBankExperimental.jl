リスニングソケットによって呼び出され、リスナーのacceptが正常に初期化されたか、エラーが発生した場合です。リスナーが成功した場合、error*codeはAWS*ERROR*SUCCESSとなり、ソケットはすでに[`aws*socket*start*accept`](@ref)()で指定されたイベントループに割り当てられています。

エラーが発生した場合、error_codeはゼロ以外の値になります。
