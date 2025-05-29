```
hbnlsolve(w::NTuple{N,Number}, sources, frequencies::Frequencies{N},
    indices::FourierIndices{N}, psc::ParsedSortedCircuit, cg::CircuitGraph,
    nm::CircuitMatrices; iterations = 1000, x0 = nothing,
    ftol = 1e-8, switchofflinesearchtol = 1e-5, alphamin = 1e-4,
    symfreqvar = nothing)
```

New version of the nonlinear harmonic balance solver suitable for arbitrary numbers of ports, sources, and drives including direct current (zero frequency) or flux pumping using a current source and a mutual inductor.

# Examples

```jldoctest
circuit = Tuple{String,String,String,Union{Complex{Float64},Symbol,Int64}}[]
push!(circuit,("P1","1","0",1))
push!(circuit,("R1","1","0",:Rleft))
push!(circuit,("L1","1","0",:Lm)) 
push!(circuit,("K1","L1","L2",:K1))
push!(circuit,("C1","1","2",:Cc)) 
push!(circuit,("L2","2","3",:Lm)) 
push!(circuit,("Lj3","3","0",:Lj)) 
push!(circuit,("Lj4","2","0",:Lj)) 
push!(circuit,("C2","2","0",:Cj))
circuitdefs = Dict{Symbol,Complex{Float64}}(
    :Lj =>2000e-12,
    :Lm =>10e-12,
    :Cc => 200.0e-15,
    :Cj => 900e-15,
    :Rleft => 50.0,
    :Rright => 50.0,
    :K1 => 0.9,
)

Idc = 50e-5
Ip=0.0001e-6
wp=2*pi*5e9
Nharmonics = (2,)
frequencies = JosephsonCircuits.removeconjfreqs(
    JosephsonCircuits.truncfreqs(
        JosephsonCircuits.calcfreqsrdft(Nharmonics),
        dc=true, odd=true, even=false, maxintermodorder=Inf,
    )
)
fi = JosephsonCircuits.fourierindices(frequencies)
Nmodes = length(frequencies.modes)
psc = JosephsonCircuits.parsesortcircuit(circuit)
cg = JosephsonCircuits.calccircuitgraph(psc)
nm = JosephsonCircuits.numericmatrices(psc, cg, circuitdefs, Nmodes = Nmodes)

out=hbnlsolve(
    (wp,),
    [
        (mode=(0,),port=1,current=Idc),
        (mode=(1,),port=1,current=Ip),
    ],
    frequencies, fi, psc, cg, nm)
isapprox(out.nodeflux[:],
    ComplexF64[15.190314040027522 - 8.56492651167657e-24im, 2.991103820177504e-6 - 1.8501001011477133e-8im, -6.835392148510984 - 1.0356102442254259e-14im, 7.396422335315908e-6 - 4.5749403967992827e-8im, 6.835392148539885 - 1.0356102451770844e-14im, 1.008026285172782e-5 - 6.23498762664213e-8im],
    atol = 1e-6)

# output
true
```
