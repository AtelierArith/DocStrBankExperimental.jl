```
get_transpiler(qpu::AbstractQPU)::Transpiler
```

Returns the transpiler associated with this QPU.

# Example

```jldoctest
julia> qpu = AnyonYukonQPU(client, "project_id");

julia> get_transpiler(qpu)
SequentialTranspiler(Transpiler[CircuitContainsAReadoutTranspiler(), ReadoutsDoNotConflictTranspiler(), UnsupportedGatesTranspiler(), DecomposeSingleTargetSingleControlGatesTranspiler(), CastToffoliToCXGateTranspiler(), CastCXToCZGateTranspiler(), CastISwapToCZGateTranspiler(), CastRootZZToZ90AndCZGateTranspiler(), SwapQubitsForAdjacencyTranspiler(LineConnectivity{6}
1──2──3──4──5──6
), CastSwapToCZGateTranspiler()  …  SimplifyTrivialGatesTranspiler(1.0e-6), CastUniversalToRzRxRzTranspiler(), SimplifyRxGatesTranspiler(1.0e-6), CastRxToRzAndHalfRotationXTranspiler(), CompressRzGatesTranspiler(), SimplifyRzGatesTranspiler(1.0e-6), ReadoutsAreFinalInstructionsTranspiler(), RejectNonNativeInstructionsTranspiler(LineConnectivity{6}
1──2──3──4──5──6
, DataType[Snowflurry.Identity, Snowflurry.PhaseShift, Snowflurry.Pi8, Snowflurry.Pi8Dagger, Snowflurry.SigmaX, Snowflurry.SigmaY, Snowflurry.SigmaZ, Snowflurry.X90, Snowflurry.XM90, Snowflurry.Y90, Snowflurry.YM90, Snowflurry.Z90, Snowflurry.ZM90, Snowflurry.ControlZ]), RejectGatesOnExcludedPositionsTranspiler(LineConnectivity{6}
1──2──3──4──5──6
), RejectGatesOnExcludedConnectionsTranspiler(LineConnectivity{6}
1──2──3──4──5──6
)])
```
