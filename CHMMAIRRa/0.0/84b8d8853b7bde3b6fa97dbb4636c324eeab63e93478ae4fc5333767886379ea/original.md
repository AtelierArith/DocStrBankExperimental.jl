```
detect_chimeras(refnames::Vector{String}, refseqs::Vector{String}, assignments::DataFrame;
                HMM_parameters::Union{Dict, Nothing} = nothing,
                p_threshold::Float64 = 0.95,
                receptor::String = "IG",

                chimeric_alignments::Bool = false,
                recombfreqplot::Bool = false,
                detailed::Bool = false,
                subsample::Union{Int, Nothing} = nothing,
                deduplicate::Bool = false,

                count_chimeric_segments::Bool = false,
                trim::Int = 5,
                seed::Int = 123,

                mafft::Union{String, Nothing} = nothing,
                align_database::Bool = false,

                quiet::Bool = false,
                disable_internal_dedup::Bool = false
                )::NamedTuple{(:out, :chimeric_alignments, :recombfreqplot),
                            Tuple{DataFrame,
                            Union{Nothing, Tuple{Vector{String}, Vector{String}}},
                            Any}
                            }
                }
```

Run CHMMAIRRa on parsed arguments, returning output as a Tuple containing relevant outputs. Output tuple fields:

1. out: the input assignments dataframe with chimerism probabilities.
2. chimeric*alignments: names and sequences for alignments showing which reference sequences recombined at which positions to form detected chimeras. Set to nothing if chimeric*alignments is false.
3. recombfreqplot: barplot of most frequent recombinations, normalized by their expected frequencies. Set to nothing if recombfreqplot is false.

# Arguments:

  * `refnames::Vector{String}`: Names of the reference sequences.
  * `refseqs::Vector{String}`: Sequences of the reference sequences.
  * `assignments::DataFrame`: VDJ assignments, in MiAIRR format.

# Optional arguments:

  * `HMM_parameters::Union{Dict, Nothing}`: If set, use HMM parameters in this dictionary. Overrides parameter presets from receptor.
  * `p_threshold::Float64`: Posterior threshold of switching templates.
  * `receptor::String`: Which adaptive immune receptor to run on. Options: IG, TCR.
  * `chimeric_alignments::Bool`: Whether to generate and return chimeric sequences and the germline alignments they matched to.
  * `recombfreqplot::Bool`: Whether to generate and return a plot of chimerism per recombination event.
  * `detailed::Bool`: Whether to include details about the chimeras. Calculate viterbi path for chimeric sequences to add startingpoint, recombinations, recombinations*degapped, and max*log_prob columns.
  * `subsample::Union{Int, Nothing}`: Randomly subsample this number of unique sequences to run chimera detection on.
  * `deduplicate::Bool`: Whether to deduplicate input by v*sequence*alignment column. Note that if subsample is given, subsampling is performed after deduplication.
  * `count_chimeric_segments::Bool`: If set, count the number of times chimeric segments appear in nonchimeric sequences. Adds chimera*segment*counts column.
  * `trim::Int`: How many nucleotides to trim off the inner ends of the chimeric segments when searching for matches in nonchimeric sequences.
  * `seed::Int`: Seed to use for random subsampling.
  * `mafft::Union{String, Nothing}`: Path to MAFFT binary. If not provided, will try to find mafft in system PATH.
  * `align_database::Bool`: Whether to align database V sequences.
  * `quiet::Bool`: If set, hides non-error messages.
  * `disable_internal_dedup::Bool`: If set, does not deduplicate sequences internally. This was added for timing benchmark purposes and has no effect on the output.
