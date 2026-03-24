# ZackAI 🤖

A custom general assistant AI model trained using [Unsloth](https://github.com/unslothai/unsloth) on a free Kaggle T4 GPU. The finished model is exported as a ~4 GB GGUF file that loads directly into [LM Studio](https://lmstudio.ai).

---

## Model Details

| Property | Value |
|---|---|
| **Base model** | [Qwen 2.5 3B](https://huggingface.co/unsloth/Qwen2.5-3B) |
| **Training method** | LoRA fine-tuning via Unsloth |
| **Dataset** | [teknium/OpenHermes-2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5) |
| **Quantization** | Q4_K_M (GGUF, ~4 GB) |
| **Hardware** | Kaggle free T4 GPU |
| **Identity** | Responds as "ZackAI, a helpful, harmless, and honest AI assistant created by Zack" |

---

## Step-by-Step: Train & Run ZackAI

### 1 — Create a Hugging Face Account & API Token

1. Go to <https://huggingface.co> and sign up for a free account.
2. Open **Settings → Access Tokens → New token**.
3. Give it a name (e.g. `kaggle-zackai`), select **Write** permission, and click **Generate**.
4. Copy the token — you will paste it into the notebook in step 4.

---

### 2 — Open the Notebook on Kaggle

1. Go to <https://www.kaggle.com> and sign in (create a free account if needed).
2. Click **Create → New Notebook**.
3. In the new notebook, click **File → Import Notebook**.
4. Upload `train_zackai.ipynb` from this repository (or paste the GitHub raw URL).

---

### 3 — Enable the T4 GPU

1. In the Kaggle notebook, open the **Settings** panel on the right.
2. Under **Accelerator**, select **GPU T4 x2**.
3. Make sure **Internet** is turned **On** (required to download the dataset and upload to HF).

---

### 4 — Set Your HF_TOKEN and HF_USERNAME

At the very top of the notebook there is a cell labelled **"🔑 Configuration — Set Your Credentials Here"**.  
Edit the two variables:

```python
HF_TOKEN    = "hf_YOUR_TOKEN_HERE"
HF_USERNAME = "your-huggingface-username"
```

---

### 5 — Run All Cells & Close the Tab

1. Click **Run All** (▶▶ button or **Run → Run All**).
2. You can safely **close the browser tab** — Kaggle keeps the session running in the background.
3. Training takes approximately **4–6 hours** on a free T4 GPU.
4. When finished, the GGUF model is automatically uploaded to  
   `https://huggingface.co/{HF_USERNAME}/ZackAI`

---

### 6 — Download the GGUF from Hugging Face

1. Go to `https://huggingface.co/{HF_USERNAME}/ZackAI`.
2. Click the **Files and versions** tab.
3. Download the file ending in `Q4_K_M.gguf` (~4 GB).

---

### 7 — Load into LM Studio

1. Open **LM Studio** and go to the **My Models** tab.
2. Click **Add Model → From File** and select the downloaded `.gguf` file.
3. Click **Load** — ZackAI is ready to chat! 🎉

---

## Hardware Requirements

| Requirement | Free Tier Value |
|---|---|
| Platform | Kaggle |
| GPU | NVIDIA T4 (16 GB VRAM) |
| Weekly GPU hours | 30 hours |
| RAM | ~13 GB |
| Disk | 20 GB |

Training uses **4-bit quantization + LoRA** so the model fits comfortably in 16 GB VRAM.

---

## Repository Files

| File | Description |
|---|---|
| `train_zackai.ipynb` | Kaggle-ready Unsloth training notebook |
| `requirements.txt` | Python dependencies (for reference) |
| `.gitignore` | Ignores model outputs, cache, GGUF files |
| `LICENSE` | Apache 2.0 |

---

## License

This project is licensed under the **Apache 2.0 License** — see [LICENSE](LICENSE) for details.

---

## Credits

- **[Unsloth](https://github.com/unslothai/unsloth)** — 2× faster fine-tuning with 70% less memory
- **[Qwen 2.5](https://huggingface.co/Qwen)** — Base model by Alibaba Cloud
- **[OpenHermes-2.5](https://huggingface.co/datasets/teknium/OpenHermes-2.5)** — High-quality general assistant dataset by Teknium
- **[LM Studio](https://lmstudio.ai)** — Local model runner
