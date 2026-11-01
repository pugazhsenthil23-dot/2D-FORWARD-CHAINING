# 2D-FORWARD-CHAINING# Experiment 2(d) – Implementation of Forward Chaining

## Aim

To implement forward chaining.

## Scenario

A diagnostic expert system helps determine whether a patient has a disease based on observed symptoms. The system uses forward chaining, where it starts with known facts (symptoms) and applies rules to infer new facts until it reaches a conclusion (diagnosis).

## Procedure

1. Initialize a knowledge base containing IF-THEN rules.
2. Define the initial facts (observed symptoms or given conditions).
3. Repeat until no new facts are inferred:

   * Iterate through each rule in the knowledge base.
   * Check if all conditions (IF part) of a rule exist in the known facts.
   * If true and the conclusion (THEN part) is not already in facts, add it to the facts.
   * Mark that a new fact was inferred and continue.
4. Stop when no new facts are derived in an iteration.
5. Check if the final goal or diagnosis is in the inferred facts.
6. Output the conclusion based on derived facts.

## Program

```python
# Knowledge Base: Rules in IF-THEN format
knowledge_base = [
    (["cough", "fever"], "flu"),
    (["sore_throat", "runny_nose"], "cold"),
    (["sore_throat"], "fever")
]

# Given initial facts
facts = {"cough", "sore_throat"}

# Forward Chaining Function
def forward_chaining():
    inferred = True

    while inferred:
        inferred = False

        for conditions, conclusion in knowledge_base:
            if all(condition in facts for condition in conditions) and conclusion not in facts:
                facts.add(conclusion)
                inferred = True

# Run forward chaining
forward_chaining()

# Check if flu or cold is inferred
if "flu" in facts:
    print("The patient is diagnosed with flu.")
elif "cold" in facts:
    print("The patient is diagnosed with cold.")
else:
    print("No conclusive diagnosis could be made.")
```

## Output

```text
The patient is diagnosed with flu.
```

## Result

Thus, the forward chaining algorithm was implemented successfully using Python. The system inferred new facts from the initial symptoms and diagnosed the patient with flu.
