LSTM Text Generation

📌 Project Description

This project implements a character-level text generation model trained on the complete Shakespeare corpus. The goal is to learn how sequence models process sequential data and generate text in a specific writing style.
The model is trained to predict the next character given a sequence of previous characters, allowing it to generate new text that mimics Shakespeare’s tone, structure, and vocabulary.

🧠 Architecture Explanation

The model uses a standard sequence modeling architecture based on LSTM (Long Short-Term Memory) networks:

1. Embedding Layer
Maps each character to a dense vector representation.

2. LSTM Layer 1 (512 units)
Processes the input sequence and returns a sequence of hidden states, allowing the model to capture temporal patterns.

3. LSTM Layer 2 (512 units)
Produces a final context vector summarizing the entire input.

4. Dense Output Layer (softmax)
Outputs a probability distribution over all possible characters, indicating which character should come next.

Training objective: categorical cross-entropy between predicted and true next characters.
Sampling: generation is performed using temperature scaling to adjust randomness.

▶️ How to Run the Code

1. Install dependencies

pip install tensorflow numpy


2. Run the notebook or script
The model automatically downloads the Shakespeare dataset:

path_to_file = tf.keras.utils.get_file(
    "shakespeare.txt",
    "https://storage.googleapis.com/download.tensorflow.org/data/shakespeare.txt"
)


Execute all cells in the notebook (or run the Python script).
Training uses an LSTM over sequences of 100 characters.

3. Generate text
After training, call:

generate_text("Shall I compare thee", temperature=1.0)


You can experiment with different temperatures (0.5, 1.0, 1.5).

📊 Results and Analysis

The model was trained for 3 epochs, achieving a steady decrease in training loss:

Epoch 1: ~1.83

Epoch 2: ~1.33

Epoch 3: ~1.26

Even with only a few epochs, the model successfully learned patterns characteristic of Shakespeare’s writing—line structure, punctuation style, and common words.

===== Generated Text (Temp = 0.5) =====

Shall I compare thee:
I am ancient time and state and follow'd.

PETRUCHIO:
All this is the day of men are sorrow.

CLARENCE:
I do not be a strength to my son of me.

CLARENCE:
Farewell, come hither, come.

AUTOLYCUS:
I 

===== Generated Text (Temp = 1.0) =====

Shall I compare thee:
And tell you, siely and his worn of fear
A bell, he doth raised aallianton
Than in the child. No, I'll come on him:
And in these child, made a little shall
hear it, and in my bristal men I must now,

===== Generated Text (Temp = 1.5) =====

Shall I compare thee, in why,--
Hare, nories homing? why cut him learncelly
Think thee to his kitw? a' callar
Off; but, leoss--youchen; ore 'tis elsener,--
SciliCuld, be leong witch her adved Richmond?.
Hark looks helven

Low temperature produces structured and predictable text,
while higher temperature leads to more surprising and creative outputs.
Overall, the model demonstrates how LSTMs can learn stylistic patterns purely from sequential character data.
