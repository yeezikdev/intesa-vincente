# Intesa Vincente

Il gioco dell'Intesa Vincente (Reazione a Catena) per **3 telefoni collegati in tempo reale**.
Due suggeritori vedono la parola e ne dicono una a testa, il terzo deve indovinarla prima che scada il tempo.

## Come si gioca

1. Uno apre il sito e tocca **Crea partita**: compare un codice di 4 lettere.
2. Gli altri due aprono lo stesso sito sul loro telefono e inseriscono il codice.
3. Ognuno sceglie il ruolo: **Suggeritore 1**, **Suggeritore 2** o **Indovino** (si può aggiungere anche uno **Spettatore**).
4. Chi ha creato la partita sceglie il tempo (60–120 secondi) e preme **Via!**
5. I suggeritori dicono una parola a testa, alternandosi. L'indovino preme **Prenota** per fermare il tempo e risponde.
6. I suggeritori segnano **Giusta** o **Sbagliata**. Ci sono **3 passo** per manche.

C'è anche la modalità **Gioca su un solo dispositivo**, che non ha bisogno di internet dopo il caricamento.

## Pubblicarlo su GitHub Pages

1. Crea un nuovo repository pubblico su GitHub (es. `intesa-vincente`).
2. Carica `index.html` e `README.md` (pulsante **Add file → Upload files**).
3. Vai su **Settings → Pages**, in *Build and deployment* scegli **Deploy from a branch**, branch `main`, cartella `/ (root)`, e salva.
4. Dopo circa un minuto il gioco è online su `https://TUO-NOME-UTENTE.github.io/intesa-vincente/`.

## Come funziona il collegamento

Il sito è una sola pagina statica, senza server proprio. I telefoni si parlano attraverso il server MQTT pubblico e gratuito di HiveMQ (`broker.hivemq.com`), usando un canale diverso per ogni codice partita.

- Il telefono di chi crea la partita tiene il punteggio, il tempo e le parole, e li invia agli altri.
- Se chi ha creato la partita chiude la pagina, la partita si interrompe.
- Il server è pubblico: non è adatto a dati privati, ma per un gioco va benissimo.

Per usare un altro server MQTT, cambia la costante `BROKER` all'inizio dello script in `index.html`.
