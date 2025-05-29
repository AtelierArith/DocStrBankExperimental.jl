```
transpile(transpiler::Transpiler, circuit::QuantumCircuit)::QuantumCircuit
```

`circuit`のトランスパイルされたコピーを返します。トランスパイルプロセスは`transpiler`に依存します。

以下のトランスパイラが利用可能です：

  * [`SequentialTranspiler`](@ref)
  * [`CompressSingleQubitGatesTranspiler`](@ref)
  * [`CastSwapToCZGateTranspiler`](@ref)
  * [`CastCXToCZGateTranspiler`](@ref)
  * [`CastISwapToCZGateTranspiler`](@ref)
  * [`CastToffoliToCXGateTranspiler`](@ref)
  * [`CastRootZZToZ90AndCZGateTranspiler`](@ref)
  * [`CastToPhaseShiftAndHalfRotationXTranspiler`](@ref)
  * [`CastUniversalToRzRxRzTranspiler`](@ref)
  * [`CastRxToRzAndHalfRotationXTranspiler`](@ref)
  * [`SimplifyRxGatesTranspiler`](@ref)
  * [`SwapQubitsForAdjacencyTranspiler`](@ref)
  * [`SimplifyRzGatesTranspiler`](@ref)
  * [`CompressRzGatesTranspiler`](@ref)
  * [`RemoveSwapBySwappingGatesTranspiler`](@ref)
  * [`SimplifyTrivialGatesTranspiler`](@ref)
  * [`UnsupportedGatesTranspiler`](@ref)
  * [`ReadoutsAreFinalInstructionsTranspiler`](@ref)
  * [`CircuitContainsAReadoutTranspiler`](@ref)
  * [`ReadoutsDoNotConflictTranspiler`](@ref)
  * [`DecomposeSingleTargetSingleControlGatesTranspiler`](@ref)
  * [`RejectNonNativeInstructionsTranspiler`](@ref)
  * [`RejectGatesOnExcludedPositionsTranspiler`](@ref)
  * [`RejectGatesOnExcludedConnectionsTranspiler`](@ref)

# 例

```jldoctest
julia> transpiler = CastCXToCZGateTranspiler();

julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [control_x(1, 2)])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──*──
       |
q[2]:──X──

julia> transpile(transpiler, circuit)
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:───────*───────
            |
q[2]:──H────Z────H──

```
