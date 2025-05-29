function to*braket*ahs*ir(bloqade*task::BloqadeSchema.QuEraTaskSpecification)

`bloqade_task`をAWS Braketに提出してQPUで実行できる`Braket.IR.AHSProgram`に変換します。

注意: `BloqadeSchema.QuEraTaskSpecification`には`Braket.IR.AHSProgram`に対応するフィールドがない`nshots`というフィールドが含まれています。この値は、`Braket.AwsDevice`インスタンスに別途キーワード引数として渡す必要があります。
