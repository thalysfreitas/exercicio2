# exercicio2
INTEGRAÇÃO COM SERVIÇO DE NUVEM

const Ajv = require("ajv");

const ajv = new Ajv();
const validate = ajv.compile({
  type: "object",
  required: ["id", "name", "unidade"],
  properties: {
    id: { type: "number" },
    name: { type: "string" },
    unidade: { type: "string" }
  }
});

// ...

function isValid(device){
  return validate(device) === true;
}

app.post("/devices", (req, res) => {
  const device = req.body
  if (!isValid(device)) {
    res.status(400).json({msg: "Dispositivo inválido!!"})
    return;
  }

  // ...
});

app.put('/devices', (req, res) => {
  const device = req.body
  if (!isValid(device)) {
    res.status(400).json({msg: "Dispositivo inválido!!"})
    return;
  }

  // ...
})


