# Form-with-Jquery-ViaCep
Formulario basico com Jquery


<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@ViewBag.Title - ViewBag passando Object</title>
    <!-- Adicionando JQuery -->
    <script src="https://code.jquery.com/jquery-3.2.1.min.js"
            integrity="sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4="
            crossorigin="anonymous">
    </script>
     <!-- Adicionando Javascript -->
    <script type="text/javascript" >

        $(document).ready(function() {
            
			$("input").on({focus:function(){
			$(this).css("background-color", "gray");},
			blur:function(){
			$(this).css("background-color", "yellow");}
			});
			
			/*$("input").blur(function(){
			$(this).css("background-color", "yellow");
			});
			
			$("input").focus(function(){
			$(this).css("background-color", "gray");
			});*/
			
            $("#btn1").click(function(){
			if($("#cep1"))			
				var cep = $("#cep1").val();
				BuscaCep(cep,1);
			});
			$("#btn2").click(function() {
			if($("#cep2"))
                var cep = $("#cep2").val();
				BuscaCep(cep,2);
			});
			
			$("#btn3").click(function() {
			if($("#cep3"))
                var cep = $("#cep3").val();
				BuscaCep(cep,3);
			});	
			
			function BuscaCep(cep, btn){
                //Verifica se campo cep possui valor informado.
				console.log(cep);
				console.log(btn);
                if (cep != "") {
                    $.getJSON("https://viacep.com.br/ws/"+ cep +"/json/?callback=?", function(dados) {
							
                            if (!("erro" in dados)) {
                                //Atualiza os campos com os valores da consulta.
                                $("#rua"+btn).val(dados.logradouro);
								$("#bairro"+btn).val(dados.bairro);
                                $("#cidade"+btn).val(dados.localidade);
                                $("#uf"+btn).val(dados.uf);
                                $("#ibge"+btn).val(dados.ibge);
                            } //end if.
                        });
                    }
                }
        });

    </script>
</head>
<body>
    <!-- Inicio do formulario -->
      <form method="get" action="">
        <label>Cep1:
        <input name="cep" type="text" id="cep1" value="" size="10" maxlength="9" /></label>
		<input type="button" id="btn1" value="Search"/><br />
        <label>Rua1:
        <input name="rua" type="text" id="rua1" size="60" /></label><br />
        <label>Bairro1:
        <input name="bairro" type="text" id="bairro1" size="40" /></label><br />
        <label>Cidade1:
        <input name="cidade" type="text" id="cidade1" size="40" /></label><br />
        <label>Estado1:
        <input name="uf" type="text" id="uf1" size="2" /></label><br />
        <label>IBGE1:
        <input name="ibge" type="text" id="ibge1" size="8" /></label><br />
      </form>
	  <hr/>
	  <form method="get" action="">
        <label>Cep2:
        <input name="cep" type="text" id="cep2" value="" size="10" maxlength="9" /></label>
		<input type="button" id="btn2" value="Search"/><br />
        <label>Rua2:
        <input name="rua" type="text" id="rua2" size="60" /></label><br />
        <label>Bairro2:
        <input name="bairro" type="text" id="bairro2" size="40" /></label><br />
        <label>Cidade2:
        <input name="cidade" type="text" id="cidade2" size="40" /></label><br />
        <label>Estado2:
        <input name="uf" type="text" id="uf2" size="2" /></label><br />
        <label>IBGE2:
        <input name="ibge" type="text" id="ibge2" size="8" /></label><br />
      </form>
	  <hr/>
	  <form method="get" action="">
        <label>Cep3:
        <input name="cep" type="text" id="cep3" value="" size="10" maxlength="9" /></label>
		<input type="button" id="btn3" value="Search"/><br />
        <label>Rua3:
        <input name="rua" type="text" id="rua3" size="60" /></label><br />
        <label>Bairro3:
        <input name="bairro" type="text" id="bairro3" size="40" /></label><br />
        <label>Cidade3:
        <input name="cidade" type="text" id="cidade3" size="40" /></label><br />
        <label>Estado3:
        <input name="uf" type="text" id="uf3" size="2" /></label><br />
        <label>IBGE3:
        <input name="ibge" type="text" id="ibge3" size="8" /></label><br />
      </form>
</body>
</html>
