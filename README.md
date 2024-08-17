# NFA to DFA Converter with String Validation

This Python script converts a Non-deterministic Finite Automaton (NFA) into a Deterministic Finite Automaton (DFA) and then checks whether given input strings are accepted by the DFA.

## Features

- **NFA to DFA Conversion**: Converts an NFA to its equivalent DFA using epsilon-closures and state transitions.
- **String Validation**: Validates input strings against the generated DFA to determine if they are accepted.

## How It Works

1. **Input Parsing**:
   - The script starts by reading the number of states, alphabet symbols, the number of transitions, and the number of strings to check.
   - The alphabet symbols, starting state, and accepting states are then read from the input.
   - Transitions are then read, including epsilon transitions (represented by the symbol `$`).

2. **Epsilon-Closure Calculation**:
   - The epsilon-closure of the starting state is computed to include all states reachable through epsilon transitions.

3. **NFA to DFA Conversion**:
   - Using the epsilon-closure and transitions, the script builds a DFA that corresponds to the input NFA.
   - States are mapped from sets of NFA states to unique DFA states.
   - Transitions for each symbol in the alphabet are computed, considering possible epsilon transitions.

4. **DFA Output**:
   - The script outputs the DFA's transitions, indicating which states are accepting.

5. **String Validation**:
   - The script reads a number of strings and checks whether each string is accepted by the DFA.
   - If a string is accepted, it prints "Yes"; otherwise, it prints "No".

## Input Format

- The first line of input contains five integers: `q s a m n`, where:
  - `q`: Number of states in the NFA.
  - `s`: Size of the alphabet.
  - `a`: Number of accepting states.
  - `m`: Number of transitions in the NFA.
  - `n`: Number of strings to validate.
- The second line contains `s` alphabet symbols separated by spaces.
- The third line contains the starting state.
- The fourth line contains the accepting states.
- The next `m` lines contain the transitions in the form: `from_state symbol to_states`, where `to_states` is a comma-separated list of states.
- The final `n` lines contain the strings to validate.

## Example Usage

```bash
python nfa_to_dfa.py
```

### Sample Input

```
5 2 2 7 3
a b
0
2 4
0 a 1
0 $ 2
1 b 1
1 a 0
2 a 3
3 b 4
4 b 3
```

### Sample Strings

```
ab
aa
aab
```

### Sample Output

```
DFA transitions:
0 --a--> 1
1 --b--> 1
1 --a--> 0
2 --a--> 3
3 --b--> 4 (accepting)
4 --b--> 3 (accepting)

Checking strings:
Yes
No
Yes
```
