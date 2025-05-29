```
status = finufft_destroy!(plan::finufft_plan{T}) where T <: finufftReal
```

これはFINUFFTプランオブジェクトを破棄します：すべての保存されたFFTWプラン、非一様点ソート配列、カーネルフーリエ変換配列、およびその他の割り当てを解放し、プランポインタをヌルにします。

整数のステータスコードが返され、成功した場合は0になります。すでに破棄されたプランを破棄しようとすると、1が返されます（finufft_destroyに関するFINUFFTのドキュメントを参照してください）。
