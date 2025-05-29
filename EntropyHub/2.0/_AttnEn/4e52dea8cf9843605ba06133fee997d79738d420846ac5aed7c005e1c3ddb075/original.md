```
  Av4, (Hxx,Hnn,Hxn,Hnx) = AttnEn(Sig)
```

Returns the attention entropy (`Av4`) calculated as the average of the   sub-entropies (`Hxx`,`Hxn`,`Hnn`,`Hnx`) estimated from the data sequence   (`Sig`) using a base-2 logarithm.

```
  Av4, (Hxx, Hnn, Hxn, Hnx) = AttnEn(Sig::AbstractArray{T,1} where T<:Real; Logx::Real=2)
```

Returns the attention entropy (`Av4`) and the sub-entropies (`Hxx`,`Hnn`,`Hxn`,`Hnx`)   from the data sequence (`Sig`) where,   Hxx:    entropy of local-maxima intervals   Hnn:    entropy of local minima intervals   Hxn:    entropy of intervals between local maxima and subsequent minima   Hnx:    entropy of intervals between local minima and subsequent maxima

# Arguments:

`Logx`  - Logarithm base, a positive scalar               (Enter 0 for natural logarithm)

See also `EnofEn`, `SpecEn`, `XSpecEn`, `PermEn`, `MSEn`

# References:

```
  [1] Jiawei Yang, et al.,
      "Classification of Interbeat Interval Time-series Using 
      Attention Entropy." 
      IEEE Transactions on Affective Computing 
      (2020)
```
