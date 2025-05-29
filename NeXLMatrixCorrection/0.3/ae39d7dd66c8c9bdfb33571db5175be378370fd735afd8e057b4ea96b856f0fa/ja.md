```
estimatecoating(substrate::Material, coating::Material, kcoating::KRatio, mc::Type{<:MatrixCorrection}=XPP)::Film
```

測定されたk比を使用して、指定された基板上のコーティング材料の質量厚を推定します。結果はFilmとして返され、基板に関連するk比の:Coatingプロパティに割り当てることができます。

前提条件：

  * コーティングは未知のすべての測定に対して同じである
  * コーティング元素のk比は最も明るい線に割り当てられていると仮定される
