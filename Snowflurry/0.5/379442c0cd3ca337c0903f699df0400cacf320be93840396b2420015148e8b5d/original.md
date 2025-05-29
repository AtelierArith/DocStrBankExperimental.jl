```
get_status(client::Client,circuitID::String)::Tuple{Status,Dict{String,Int}}
```

Obtain the status of a circuit computation which uses a `client` for connection to a `QPU` service. See [`Status`](@ref) for more details about possible statuses.

In the case of status["type"]=="FAILED", the server error is contained in status["message"].

In the case of status["type"]=="SUCCEEDED", the second element in the return tuple is  the histogram of the job results, as computed on the `QPU`, and the third element is the  job's execution time on the `QPU`, in milliseconds. 

# Example

```jldoctest
julia> circuit = QuantumCircuit(
            qubit_count = 3,
            instructions = [sigma_x(3), control_z(2, 1),
            readout(1, 1)]
        );

julia> jobID = submit_job(submit_job_client, circuit, 100, "project_id", "yukon")
"8050e1ed-5e4c-4089-ab53-cccda1658cd0"

julia> get_status(submit_job_client, jobID)
(Status: SUCCEEDED
, Dict("001" => 100), 542)

```
