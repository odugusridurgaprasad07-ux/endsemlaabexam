<!DOCTYPE html>
<html>
<head>
    <title>Image Upload & Preview</title>
    <style>
        body {
            font-family: Arial;
            text-align: center;
            margin-top: 40px;
        }

        img {
            margin-top: 20px;
            width: 200px;
            height: 200px;
            object-fit: cover;
            border: 2px solid #000;
            display: none;
        }
    </style>
</head>
<body>

    <h2>Simple Image Upload & Preview</h2>

    <!-- Upload Button -->
    <input type="file" id="imageUpload" accept="image/*">

    <!-- Preview Image -->
    <img id="preview">

    <script>
        const input = document.getElementById("imageUpload");
        const preview = document.getElementById("preview");

        // Load image from localStorage if exists
        const savedImage = localStorage.getItem("profileImage");
        if (savedImage) {
            preview.src = savedImage;
            preview.style.display = "block";
        }

        // When user selects an image
        input.addEventListener("change", function () {
            const file = this.files[0];
            if (!file) return;

            const reader = new FileReader();
            reader.readAsDataURL(file);

            reader.onload = function () {
                preview.src = reader.result;
                preview.style.display = "block";

                // Save to localStorage
                localStorage.setItem("profileImage", reader.result);
            }
        });
    </script>

</body>
</html>
