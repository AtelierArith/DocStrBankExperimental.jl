```
hblinsolve(w, psc::ParsedSortedCircuit,
    cg::CircuitGraph, circuitdefs, signalfreq::Frequencies{N};
    nonlinear=nothing, symfreqvar=nothing,
    nbatches::Integer = Base.Threads.nthreads(), sorting = :number,
    returnS = true, returnSnoise = false, returnQE = true, returnCM = true,
    returnnodeflux = false, returnnodefluxadjoint = false,
    returnvoltage = false,
    )
```

Harmonic balance solver supporting an arbitrary number of small signals (weak tones) linearized around `pump`, the solution of the nonlinear system consisting of an arbitrary number of large signals (strong tones).

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

Idc = 1e-6*0
Ip = 5.0e-6
wp = 2*pi*5e9
ws = 2*pi*5.2e9
Npumpharmonics = (2,)
Nmodulationharmonics = (2,)
threewavemixing = false
fourwavemixing = true

frequencies = JosephsonCircuits.removeconjfreqs(
    JosephsonCircuits.truncfreqs(
        JosephsonCircuits.calcfreqsrdft(Npumpharmonics),
        dc = true, odd = true, even = false, maxintermodorder = Inf,
    )
)
fi = JosephsonCircuits.fourierindices(frequencies)
Nmodes = length(frequencies.modes)
psc = JosephsonCircuits.parsesortcircuit(circuit)
cg = JosephsonCircuits.calccircuitgraph(psc)
nm = JosephsonCircuits.numericmatrices(psc, cg, circuitdefs, Nmodes = Nmodes)
nonlinear = hbnlsolve(
    (wp,),
    [
        (mode=(0,),port=1,current=Idc),
        (mode=(1,),port=1,current=Ip),
    ],
    frequencies, fi, psc, cg, nm)
signalfreq =JosephsonCircuits.truncfreqs(
    JosephsonCircuits.calcfreqsdft(Nmodulationharmonics),
    dc = true, odd = threewavemixing, even = fourwavemixing,
    maxintermodorder = Inf,
)
linearized = JosephsonCircuits.hblinsolve(ws, psc, cg, circuitdefs,
    signalfreq;nonlinear = nonlinear, returnnodeflux=true, keyedarrays = Val(false))
isapprox(linearized.nodeflux,
    ComplexF64[9.901008591291e-12 - 6.40587007644028e-14im 2.164688307719963e-14 - 2.90852607344097e-16im 6.671563044645655e-14 - 8.585524364135119e-16im; 2.1633104519765224e-14 - 8.251861334047893e-16im 1.0099063486905209e-11 - 1.948847859339803e-13im -8.532003011745068e-15 + 3.234788465760295e-16im; 6.671648606599472e-14 + 7.892709980649199e-16im -8.53757633177974e-15 - 9.748395563374129e-17im 9.856580758892428e-12 + 5.859984004390703e-14im; 1.5888896262186103e-11 - 1.0303480614499543e-13im -2.557126237504446e-12 + 1.759201163407723e-14im -8.475819811683215e-12 + 5.3531443609574795e-14im; -2.5781681021577177e-13 + 4.757590640631487e-15im 2.36818731889176e-12 - 4.569646499606389e-14im 1.116372367616482e-13 - 2.039935997276492e-15im; -1.0210743447568219e-11 - 5.905490368441375e-14im 1.3377918536056493e-12 + 7.190105205618706e-15im 2.5392856657302323e-11 + 1.5143842454586225e-13im; 2.4781693042536835e-11 - 1.6057018472176702e-13im -2.5342360504077476e-12 + 1.7306764301173096e-14im -8.40554044664581e-12 + 5.269404591748149e-14im; -2.348528974341763e-13 + 3.949450668269274e-15im 1.1449271118157543e-11 - 2.2093702114766968e-13im 1.0261871618968225e-13 - 1.7240213938923877e-15im; -1.0140560031409567e-11 - 5.828587508192886e-14im 1.3288225860409326e-12 + 7.0954601524623594e-15im 3.423954321087654e-11 + 2.0403371894291513e-13im],
    atol = 1e-6)

# output
true
```
