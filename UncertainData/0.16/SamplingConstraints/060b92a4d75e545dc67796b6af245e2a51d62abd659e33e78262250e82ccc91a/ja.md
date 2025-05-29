```
constrain(udata::AbstractUncertainValueDataset, 
	s::SamplingConstraint) -> ConstrainedUncertainValueDataset
```

制約`s`を`udata`内の各不確実値に適用することによって、不確実データセットを返します。
