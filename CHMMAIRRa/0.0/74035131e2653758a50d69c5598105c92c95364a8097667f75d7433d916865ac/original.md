```
detect_chimeras_from_files(V_fasta::String, assignments::String, out::String;

        p_threshold::Float64 = 0.95,
        receptor::String = "IG",

        non_chimeric_MiAIRR::Union{String, Nothing} = nothing,
        chimeric_MiAIRR::Union{String, Nothing} = nothing,
        chimeric_alignments::Union{String, Nothing} = nothing,
        recombfreqplot::Union{String, Nothing} = nothing,
        detailed::Bool = false,
        subsample::Union{Int, Nothing} = nothing,
        deduplicate::Bool = false,
        chunk_size::Union{Int, Nothing} = nothing,

        HMM_parameters::Union{String, Nothing} = nothing,
        mafft::Union{String, Nothing} = nothing,
        align_database::Bool = false,
        count_chimeric_segments::Bool = false,
        trim::Int = 5,
        seed::Int = 123,

        quiet::Bool = false,
        disable_internal_dedup::Bool = false
        )
```

Run CHMMAIRRa from input files to writing of output files, taking care of I/O.

# Arguments:

  * `V_fasta::String`: V database in fasta format.
  * `assignments::String`: VDJ assignments, in MiAIRR format.
  * `out::String`: Write CHMMAIRRa output.

# Optional arguments:

  * `p_threshold::Float64`: Posterior threshold of switching templates.
  * `receptor::String`: Which adaptive immune receptor to run on. Options: IG, TCR.
  * `non_chimeric_MiAIRR::Union{String, Nothing}`: Write assignments of sequences determined to be non-chimeric.
  * `chimeric_MiAIRR::Union{String, Nothing}`: Write assignments of sequences determined to be chimeric.
  * `chimeric_alignments::Union{String, Nothing}`: Write fasta file containing chimeric sequences and the germline alignments they matched to.
  * `recombfreqplot::Union{String, Nothing}`: Generate a plot of chimerism per recombination event.
  * `detailed::Bool`: Include details about the chimeras. Calculate viterbi path for chimeric sequences to add startingpoint, recombinations, recombinations*degapped, and max*log_prob columns.
  * `subsample::Union{Int, Nothing}`: Randomly subsample this number of unique sequences to run chimera detection on.
  * `deduplicate::Bool`: Deduplicate input by v*sequence*alignment column. Note that if subsample is given, subsampling is performed after deduplication.
  * `chunk_size::Union{Int, Nothing}`: Read in chunk-size lines of input at a time, write output for that chunk, and move to the next chunk.
  * `HMM_parameters::Union{String, Nothing}`: If set, use HMM parameters in this file. Overrides parameter presets from –receptor. See src/IG*parameters.tsv or src/TCR*parameters.tsv for formatting.
  * `mafft::Union{String, Nothing}`: Path to MAFFT binary. If not provided, will try to find mafft in system PATH.
  * `align_database::Bool`: Whether to align database V sequences.
  * `count_chimeric_segments::Bool`: If set, count the number of times chimeric segments appear in nonchimeric sequences. Adds chimera*segment*counts column.
  * `trim::Int`: How many nucleotides to trim off the inner ends of the chimeric segments when searching for matches in nonchimeric sequences.
  * `seed::Int`: Seed to use for random subsampling.
  * `quiet::Bool`: If set, hides non-error messages.
  * `disable_internal_dedup::Bool`: If set, does not deduplicate sequences internally. This was added for timing benchmark purposes and has no effect on the output.
